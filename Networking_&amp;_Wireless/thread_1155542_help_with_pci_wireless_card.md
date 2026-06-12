---
title: "help with pci wireless card"
date: 2009-05-10
forum: Networking &amp; Wireless
---

### Post by Jimshoe02 on 2009-05-10
To start off with, I am entirely new to linux. I am trying to connect my desktop to my wireless router with a pci wireless card. I am running Ubuntu 8.10 and using a Dynex DX-BGDTC card. I installed ndiswrapper and installed the windows XP driver for it. when i type ndiswrapper -l, I get both driver installed and hardware installed. I type in iwconfig and my wlan0 device shows up, but in the network configuration gui, it doesn't show up. I know you will need more information, but I don't know what at this point. Just tell me what you need and I'll go get it.

---

### Post by Jimshoe02 on 2009-05-10
I also tried configuring the device using the iwconfig switches, but dont know how to get it to connect or even if i configured everything correctly. Is there anything I need to do to enable my device or something to get it to show up in the network configuration pannel? Any help would be very appreciated.

---

### Post by Jimshoe02 on 2009-05-11
Alright. I just read the how to post a ticket sticky thread. Here's all the information it requested. Sorry I didn't see it before. 





 

1 ) Machine Brand and Model (PC/Laptop):

Home-built PC
Processor: Intel Pentium D CPU 2.80 GHz
RAM: 2.5 GB


 
2 ) Wireless Brand, Model and Wireless Chipset:
Code:

```
kyle@kyle-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
05:00.0 FireWire (IEEE 1394): Adaptec AIC-5800 (rev 10)
05:01.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
05:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)
```

3 ) check interface:
Code:

```
kyle@kyle-desktop:~$ iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
The wlan0 device resets each time I restart the computer. none of these settings are what they were before I restarted.

4 ) Check for modules:
Code:

```
kyle@kyle-desktop:~$ lsmod
Module                  Size  Used by
ipv6                  314312  14 
isofs                  44072  1 
udf                    93480  0 
crc_itu_t              10496  1 udf
af_packet              29568  2 
rfkill_input           14080  0 
binfmt_misc            18700  1 
rfcomm                 51104  0 
sco                    20612  2 
bridge                 64544  0 
stp                    11268  1 bridge
bnep                   23168  2 
l2cap                  33280  6 rfcomm,bnep
bluetooth              70820  6 rfcomm,sco,bnep,l2cap
ppdev                  16904  0 
cpufreq_stats          14468  0 
cpufreq_userspace      12420  0 
cpufreq_powersave      10368  0 
cpufreq_ondemand       16400  0 
cpufreq_conservative    16392  0 
freq_table             13568  2 cpufreq_stats,cpufreq_ondemand
sbs                    22288  0 
wmi                    15808  0 
sbshc                  14592  1 sbs
pci_slot               13704  0 
video                  28948  0 
output                 11776  1 video
container              12288  0 
battery                21128  0 
iptable_filter         11520  0 
ip_tables              28176  1 iptable_filter
x_tables               31752  1 ip_tables
ac                     13448  0 
lp                     19588  0 
arc4                   10368  2 
ecb                    11520  2 
crypto_blkcipher       27780  1 ecb
b43                   144424  0 
rfkill                 19364  2 rfkill_input,b43
serio_raw              14596  0 
mac80211              253440  1 b43
pcspkr                 11136  0 
psmouse                51612  0 
evdev                  20512  7 
cfg80211               37136  1 mac80211
led_class              13192  1 b43
snd_hda_intel         489264  3 
input_polldev          12816  1 b43
snd_pcm_oss            52608  0 
snd_mixer_oss          25088  1 snd_pcm_oss
snd_pcm                99208  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            42368  0 
snd_seq_midi           15872  0 
snd_rawmidi            34176  1 snd_seq_midi
snd_seq_midi_event     16768  2 snd_seq_oss,snd_seq_midi
parport_pc             44200  1 
snd_seq                67168  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
parport                50096  3 ppdev,lp,parport_pc
snd_timer              34320  2 snd_pcm,snd_seq
snd_seq_device         16404  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iTCO_wdt               21072  0 
iTCO_vendor_support    12420  1 iTCO_wdt
button                 15904  0 
snd                    79432  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
shpchp                 42140  0 
pci_hotplug            39472  1 shpchp
intel_agp              39280  0 
snd_page_alloc         17680  2 snd_hda_intel,snd_pcm
ext3                  150544  1 
jbd                    66472  1 ext3
mbcache                17924  1 ext3
usbhid                 39776  0 
hid                    59072  1 usbhid
sd_mod                 45864  5 
crc_t10dif             10240  1 sd_mod
sr_mod                 24644  1 
cdrom                  47784  1 sr_mod
sg                     45408  0 
ata_generic            14212  0 
pata_acpi              13568  0 
uhci_hcd               34336  0 
ehci_hcd               48908  0 
ata_piix               29444  4 
libata                200160  3 ata_generic,pata_acpi,ata_piix
scsi_mod              183160  4 sd_mod,sr_mod,sg,libata
dock                   18464  1 libata
ssb                    46340  1 b43
e100                   46096  0 
mii                    14592  1 e100
usbcore               175376  4 usbhid,uhci_hcd,ehci_hcd
thermal                27424  0 
processor              47800  1 thermal
fan                    13576  0 
fbcon                  51200  0 
tileblit               11264  1 fbcon
font                   17152  1 fbcon
bitblit                14592  1 fbcon
softcursor             10496  1 bitblit
fuse                   68288  5 
```

...... there is more

---

### Post by Jimshoe02 on 2009-05-11
5 ) Kernel boot messages
Code:

```
$ dmesg
[    0.613876] bus: 05 index 4 mmio: [0, ffffffffffffffff]
[    0.613893] NET: Registered protocol family 2
[    0.652286] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.654428] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.659873] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.660524] TCP: Hash tables configured (established 524288 bind 65536)
[    0.660530] TCP reno registered
[    0.672178] NET: Registered protocol family 1
[    0.672340] checking if image is initramfs... it is
[    1.088517] Switched to high resolution mode on CPU 1
[    1.092033] Switched to high resolution mode on CPU 0
[    1.451263] Freeing initrd memory: 8427k freed
[    1.458562] audit: initializing netlink socket (disabled)
[    1.458593] type=2000 audit(1241958461.456:1): initialized
[    1.464653] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.468387] VFS: Disk quotas dquot_6.5.1
[    1.468575] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.468732] msgmni has been set to 5021
[    1.468902] io scheduler noop registered
[    1.468905] io scheduler anticipatory registered
[    1.468908] io scheduler deadline registered
[    1.469082] io scheduler cfq registered (default)
[    1.469312] pci 0000:01:00.0: Boot video device
[    1.469329] pci 0000:05:08.0: Firmware left e100 interrupts enabled; disabling
[    1.469483] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.469523] pcieport-driver 0000:00:01.0: found MSI capability
[    1.469559] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.469683] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.469718] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.469757] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.469820] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.469939] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.469974] pcieport-driver 0000:00:1c.2: found MSI capability
[    1.470012] pci_express 0000:00:1c.2:pcie00: allocate port service
[    1.470081] pci_express 0000:00:1c.2:pcie02: allocate port service
[    1.470204] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.470240] pcieport-driver 0000:00:1c.3: found MSI capability
[    1.470277] pci_express 0000:00:1c.3:pcie00: allocate port service
[    1.470341] pci_express 0000:00:1c.3:pcie02: allocate port service
[    1.520471] Linux agpgart interface v0.103
[    1.520478] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.520662] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.521614] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.524245] brd: module loaded
[    1.524345] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.524591] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.527550] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.527559] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.552679] mice: PS/2 mouse device common for all mice
[    1.552867] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.552896] rtc0: alarms up to one month, hpet irqs
[    1.552962] cpuidle: using governor ladder
[    1.552966] cpuidle: using governor menu
[    1.553446] TCP cubic registered
[    1.553749] registered taskstats version 1
[    1.553902]   Magic number: 9:940:480
[    1.554047] rtc_cmos 00:03: setting system clock to 2009-05-10 12:27:42 UTC (1241958462)
[    1.554051] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.554054] EDD information not available.
[    1.554111] Freeing unused kernel memory: 536k freed
[    1.554418] Write protecting the kernel read-only data: 4348k
[    1.577913] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.727505] fuse init (API version 7.9)
[    1.852769] processor ACPI0007:00: registered as cooling_device0
[    1.852876] processor ACPI0007:01: registered as cooling_device1
[    2.361807] usbcore: registered new interface driver usbfs
[    2.361845] usbcore: registered new interface driver hub
[    2.372836] usbcore: registered new device driver usb
[    2.378229] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[    2.378233] e100: Copyright(c) 1999-2006 Intel Corporation
[    2.378299] e100 0000:05:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.403363] e100 0000:05:08.0: PME# disabled
[    2.410585] e100: eth0: e100_probe: addr 0xb3002000, irq 20, MAC addr 00:16:76:31:52:fa
[    2.411923] b43-pci-bridge 0000:05:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    2.414099] No dock devices found.
[    2.429269] SCSI subsystem initialized
[    2.447393] libata version 3.00 loaded.
[    2.481757] USB Universal Host Controller Interface driver v3.0
[    2.488690] ssb: Sonics Silicon Backplane found on PCI device 0000:05:01.0
[    2.488803] ata_piix 0000:00:1f.1: version 2.12
[    2.488819] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.488867] ata_piix 0000:00:1f.1: setting latency timer to 64
[    2.489437] scsi0 : ata_piix
[    2.489581] scsi1 : ata_piix
[    2.490628] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x30b0 irq 14
[    2.490632] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x30b8 irq 15
[    2.829086] ata1.00: ATAPI: SONY    DVD RW DRU-710A, BY03, max UDMA/66
[    2.829104] ata1.01: ATAPI: LITE-ON LTR-48126S, 2QS5, max UDMA/33
[    2.844986] ata1.00: configured for UDMA/66
[    2.860842] ata1.01: configured for UDMA/33
[    2.860900] ata2: port disabled. ignoring.
[    2.860955] isa bounce pool size: 16 pages
[    2.861815] scsi 0:0:0:0: CD-ROM            SONY     DVD RW DRU-710A  BY03 PQ: 0 ANSI: 5
[    2.862408] scsi 0:0:1:0: CD-ROM            LITE-ON  LTR-48126S       2QS5 PQ: 0 ANSI: 5
[    2.862563] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.862569] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    2.862618] ata_piix 0000:00:1f.2: setting latency timer to 64
[    2.864143] scsi2 : ata_piix
[    2.864283] scsi3 : ata_piix
[    2.864477] ata3: SATA max UDMA/133 cmd 0x30c8 ctl 0x30e4 bmdma 0x30a0 irq 19
[    2.864482] ata4: SATA max UDMA/133 cmd 0x30c0 ctl 0x30e0 bmdma 0x30a8 irq 19
[    3.036992] ata3.00: ATA-6: ST380817AS, 9.01, max UDMA/133
[    3.036998] ata3.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.037157] ata3.01: ATA-6: WDC WD800JD-23JNC0, 06.01C06, max UDMA/133
[    3.037161] ata3.01: 156312576 sectors, multi 16: LBA 
[    3.052961] ata3.00: configured for UDMA/133
[    3.061029] ata3.01: configured for UDMA/133
[    3.224316] ata4.00: ATA-7: WDC WD800JD-22LSA0, 06.01D06, max UDMA/133
[    3.224322] ata4.00: 156301488 sectors, multi 16: LBA48 
[    3.232323] ata4.00: configured for UDMA/133
[    3.232477] scsi 2:0:0:0: Direct-Access     ATA      ST380817AS       9.01 PQ: 0 ANSI: 5
[    3.232693] scsi 2:0:1:0: Direct-Access     ATA      WDC WD800JD-23JN 06.0 PQ: 0 ANSI: 5
[    3.232857] scsi 3:0:0:0: Direct-Access     ATA      WDC WD800JD-22LS 06.0 PQ: 0 ANSI: 5
[    3.237739] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.237752] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.237757] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.237829] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.237868] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00003080
[    3.238060] usb usb1: configuration #1 chosen from 1 choice
[    3.238099] hub 1-0:1.0: USB hub found
[    3.238110] hub 1-0:1.0: 2 ports detected
[    3.342324] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.342336] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.342341] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.342389] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.342419] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00003060
[    3.342580] usb usb2: configuration #1 chosen from 1 choice
[    3.342619] hub 2-0:1.0: USB hub found
[    3.342629] hub 2-0:1.0: 2 ports detected
[    3.549415] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.549426] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.549430] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.549472] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.549512] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00003040
[    3.549648] usb usb3: configuration #1 chosen from 1 choice
[    3.549684] hub 3-0:1.0: USB hub found
[    3.549695] hub 3-0:1.0: 2 ports detected
[    3.653456] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    3.653465] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    3.653469] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.653516] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.653555] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00003020
[    3.653687] usb usb4: configuration #1 chosen from 1 choice
[    3.653724] hub 4-0:1.0: USB hub found
[    3.653734] hub 4-0:1.0: 2 ports detected
[    3.660519] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    3.756258] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.756276] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.756282] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.756340] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.760233] ehci_hcd 0000:00:1d.7: debug port 1
[    3.760240] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    3.760251] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xb3104000
[    3.788016] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.788968] usb usb5: configuration #1 chosen from 1 choice
[    3.789676] hub 5-0:1.0: USB hub found
[    3.789688] hub 5-0:1.0: 8 ports detected
[    4.012151] scsi 0:0:0:0: Attached scsi generic sg0 type 5
[    4.012203] scsi 0:0:1:0: Attached scsi generic sg1 type 5
[    4.012253] scsi 2:0:0:0: Attached scsi generic sg2 type 0
[    4.012303] scsi 2:0:1:0: Attached scsi generic sg3 type 0
[    4.012350] scsi 3:0:0:0: Attached scsi generic sg4 type 0
[    4.085053] Driver 'sr' needs updating - please use bus_type methods
[    4.090041] Driver 'sd' needs updating - please use bus_type methods
[    4.092703] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    4.092709] Uniform CD-ROM driver Revision: 3.20
[    4.092845] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    4.093947] sr1: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    4.094037] sr 0:0:1:0: Attached scsi CD-ROM sr1
[    4.094181] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    4.094212] sd 2:0:0:0: [sda] Write Protect is off
[    4.094216] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.094269] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.094370] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    4.094399] sd 2:0:0:0: [sda] Write Protect is off
[    4.094403] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.094456] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.094462]  sda: sda1
[    4.101926] sd 2:0:0:0: [sda] Attached SCSI disk
[    4.102068] sd 2:0:1:0: [sdb] 156312576 512-byte hardware sectors (80032 MB)
[    4.102102] sd 2:0:1:0: [sdb] Write Protect is off
[    4.102106] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    4.102164] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.102261] sd 2:0:1:0: [sdb] 156312576 512-byte hardware sectors (80032 MB)
[    4.102292] sd 2:0:1:0: [sdb] Write Protect is off
[    4.102296] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    4.102352] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.102359]  sdb: sdb1 sdb2 < sdb5 >
[    4.122949] sd 2:0:1:0: [sdb] Attached SCSI disk
[    4.123071] sd 3:0:0:0: [sdc] 156301488 512-byte hardware sectors (80026 MB)
[    4.123103] sd 3:0:0:0: [sdc] Write Protect is off
[    4.123107] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    4.123281] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.123374] sd 3:0:0:0: [sdc] 156301488 512-byte hardware sectors (80026 MB)
[    4.123403] sd 3:0:0:0: [sdc] Write Protect is off
[    4.123407] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    4.123460] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.123466]  sdc: sdc1
[    4.133939] sd 3:0:0:0: [sdc] Attached SCSI disk
[    4.188027] usb 2-1: device not accepting address 2, error -71
[    4.244057] hub 2-0:1.0: unable to enumerate USB device on port 1
[    4.616017] usb 2-1: new low speed USB device using uhci_hcd and address 4
[    4.796408] usb 2-1: configuration #1 chosen from 1 choice
[    4.823275] usbcore: registered new interface driver hiddev
[    4.835758] input: Kensington      Kensington USB/PS2 Orbit as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.0/input/input2
[    4.852202] input,hidraw0: USB HID v1.10 Mouse [Kensington      Kensington USB/PS2 Orbit] on usb-0000:00:1d.1-1
[    4.852233] usbcore: registered new interface driver usbhid
[    4.852237] usbhid: v2.6:USB HID core driver
[    7.460708] PM: Starting manual resume from disk
[    7.460714] PM: Resume from partition 8:17
[    7.460717] PM: Checking hibernation image.
[    7.460896] PM: Resume from disk failed.
[    7.517730] kjournald starting.  Commit interval 5 seconds
[    7.517749] EXT3-fs: mounted filesystem with ordered data mode.
[   12.917059] udevd version 124 started
[   13.341865] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   13.400608] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.573509] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   13.592047] ACPI: Power Button (FF) [PWRF]
[   13.592155] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   13.624059] ACPI: Sleep Button (CM) [SLPB]
[   13.661881] iTCO_vendor_support: vendor-support=0
[   13.741875] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   13.741981] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0460)
[   13.742104] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   13.789837] intel_rng: Firmware space is locked read-only. If you can't or
[   13.789840] intel_rng: don't want to disable this in firmware setup, and if
[   13.789842] intel_rng: you are certain that your system has a functional
[   13.789843] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   13.897346] parport_pc 00:08: reported by Plug and Play ACPI
[   13.897409] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   14.321444] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   14.321488] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.495119] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   14.622109] b43-phy0: Broadcom 4318 WLAN found
[   14.672032] logips2pp: Detected unknown logitech mouse model 127
[   14.713708] phy0: Selected rate control algorithm 'pid'
[   14.967992] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
[   15.137964] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input6
[   16.966538] lp0: using parport0 (interrupt-driven).
[   17.179384] Adding 497972k swap on /dev/sdb1.  Priority:-1 extents:1 across:497972k
[   17.751177] EXT3 FS on sdb5, internal journal
[   18.876544] type=1505 audit(1241976480.140:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4287
[   19.065190] type=1505 audit(1241976480.328:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4292
[   19.065400] type=1505 audit(1241976480.328:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4292
[   19.233355] ip_tables: (C) 2000-2006 Netfilter Core Team
[   19.995418] ACPI: WMI: Mapper loaded
[   21.080947] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   21.251557] ppdev: user-space parallel port driver
[   22.678876] Bluetooth: Core ver 2.13
[   22.681587] NET: Registered protocol family 31
[   22.681594] Bluetooth: HCI device and connection manager initialized
[   22.681598] Bluetooth: HCI socket layer initialized
[   22.693849] Bluetooth: L2CAP ver 2.11
[   22.693857] Bluetooth: L2CAP socket layer initialized
[   22.706788] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.706796] Bluetooth: BNEP filters: protocol multicast
[   22.725999] Bridge firewalling registered
[   22.727159] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   22.738444] Bluetooth: SCO (Voice Link) ver 0.6
[   22.738452] Bluetooth: SCO socket layer initialized
[   22.850344] Bluetooth: RFCOMM socket layer initialized
[   22.851611] Bluetooth: RFCOMM TTY layer initialized
[   22.851618] Bluetooth: RFCOMM ver 1.10
[   27.061883] input: b43-phy0 as /devices/virtual/input/input7
[   27.180539] firmware: requesting b43/ucode5.fw
[   27.263711] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   27.263725] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[   27.345517] input: b43-phy0 as /devices/virtual/input/input8
[   27.452038] firmware: requesting b43/ucode5.fw
[   27.455886] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   27.455896] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[   27.704927] NET: Registered protocol family 17
[   41.685565] UDF-fs: No VRS found
[   41.703324] ISO 9660 Extensions: Microsoft Joliet Level 3
[   41.705302] ISOFS: changing to secondary root
[  114.244338] type=1503 audit(1241976575.508:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/5841/net/" pid=5841 profile="/usr/sbin/cupsd"
[  114.315282] NET: Registered protocol family 10
[  114.316524] lo: Disabled Privacy Extensions
[  114.317350] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  114.319763] type=1503 audit(1241976575.580:6): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=5841 profile="/usr/sbin/cupsd"
[  114.319778] type=1503 audit(1241976575.580:7): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=5841 profile="/usr/sbin/cupsd"
[  114.319786] type=1503 audit(1241976575.580:8): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=5841 profile="/usr/sbin/cupsd"
[  114.319794] type=1503 audit(1241976575.580:9): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=5841 profile="/usr/sbin/cupsd"
[  114.319801] type=1503 audit(1241976575.580:10): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=5841 profile="/usr/sbin/cupsd"
[  114.319808] type=1503 audit(1241976575.580:11): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=5841 profile="/usr/sbin/cupsd"
[  114.319815] type=1503 audit(1241976575.580:12): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=5841 profile="/usr/sbin/cupsd"
[  114.319823] type=1503 audit(1241976575.580:13): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=5841 profile="/usr/sbin/cupsd"
[  114.319901] type=1503 audit(1241976575.580:14): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/proc/5841/net/dev" pid=5841 profile="/usr/sbin/cupsd"
[  114.560299] ppdev0: registered pardevice
[  114.608339] ppdev0: unregistered pardevice
[  114.668252] ppdev0: registered pardevice
[  114.716046] ppdev0: unregistered pardevice
[  116.208588] ppdev0: registered pardevice
[  116.256206] ppdev0: unregistered pardevice
kyle@kyle-desktop:~$ clear

kyle@kyle-desktop:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-generic (buildd@yellow) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu10) ) #1 SMP Fri Oct 24 06:40:41 UTC 2008 (Ubuntu 2.6.27-7.14-generic)
[    0.000000] Command line: root=UUID=21222dbe-0b84-4408-b939-a3fea2063593 ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000009f023000 (usable)
[    0.000000]  BIOS-e820: 000000009f023000 - 000000009f071000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000009f071000 - 000000009fea9000 (usable)
[    0.000000]  BIOS-e820: 000000009fea9000 - 000000009fee9000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000009fee9000 - 000000009feed000 (usable)
[    0.000000]  BIOS-e820: 000000009feed000 - 000000009feff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000009feff000 - 000000009ff00000 (usable)
[    0.000000] last_pfn = 0x9ff00 max_arch_pfn = 0x3ffffffff
[    0.000000] init_memory_mapping
[    0.000000]  0000000000 - 009fe00000 page 2M
[    0.000000]  009fe00000 - 009ff00000 page 4k
[    0.000000] kernel direct mapping tables up to 9ff00000 @ 8000-d000
[    0.000000] last_map_addr: 9ff00000 end: 9ff00000
[    0.000000] RAMDISK: 377b5000 - 37fefd74
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP 000FE020, 0014 (r0 INTEL )
[    0.000000] ACPI: RSDT 9FEFDE48, 0038 (r1 INTEL  D945GTP       9B7 MSFT  1000013)
[    0.000000] ACPI: FACP 9FEFCF10, 0074 (r1 INTEL  D945GTP       9B7 MSFT  1000013)
[    0.000000] ACPI: DSDT 9FEF8010, 3FBC (r1 INTEL  D945GTP       9B7 MSFT  1000013)
[    0.000000] ACPI: FACS 9FEE5C40, 0040
[    0.000000] ACPI: APIC 9FEFCE10, 0078 (r1 INTEL  D945GTP       9B7 MSFT  1000013)
[    0.000000] ACPI: WDDT 9FEF7F90, 0040 (r1 INTEL  D945GTP       9B7 MSFT  1000013)
[    0.000000] ACPI: MCFG 9FEF7F10, 003C (r1 INTEL  D945GTP       9B7 MSFT  1000013)
[    0.000000] ACPI: ASF! 9FEFCD10, 00A6 (r32 INTEL  D945GTP       9B7 MSFT  1000013)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000009ff00000
[    0.000000] Bootmem setup node 0 0000000000000000-000000009ff00000
[    0.000000]   NODE_DATA [0000000000001000 - 0000000000005fff]
[    0.000000]   bootmap [000000000000b000 -  000000000001efdf] pages 14
[    0.000000] (6 early reservations) ==> bootmem [0000000000 - 009ff00000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 00008b8f9c]    TEXT DATA BSS ==> [0000200000 - 00008b8f9c]
[    0.000000]   #3 [00377b5000 - 0037fefd74]          RAMDISK ==> [00377b5000 - 0037fefd74]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [0000008000 - 000000b000]          PGTABLE ==> [0000008000 - 000000b000]
[    0.000000] found SMP MP-table at [ffff8800000fe680] 000fe680
[    0.000000]  [ffffe20000000000-ffffe200027fffff] PMD -> [ffff880001200000-ffff8800039fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[5] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0009f023
[    0.000000]     0: 0x0009f071 -> 0x0009fea9
[    0.000000]     0: 0x0009fee9 -> 0x0009feed
[    0.000000]     0: 0x0009feff -> 0x0009ff00
[    0.000000] On node 0 totalpages: 654847
[    0.000000]   DMA zone: 2111 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 640676 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 000000009f023000 - 000000009f071000
[    0.000000] PM: Registered nosave memory: 000000009fea9000 - 000000009fee9000
[    0.000000] PM: Registered nosave memory: 000000009feed000 - 000000009feff000
[    0.000000] Allocating PCI resources starting at a0000000 (gap: 9ff00000:60100000)
[    0.000000] PERCPU: Allocating 64928 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 642787
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=21222dbe-0b84-4408-b939-a3fea2063593 ro quiet splash 
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PMTIMER calibration value
[    0.000000] Detected 2799.935 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Calgary: detecting Calgary via BIOS EBDA area
[    0.004000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.004000] Memory: 2562636k/2620416k available (3112k kernel code, 56752k reserved, 1575k data, 536k init)
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004013] Calibrating delay loop (skipped), value calculated using timer frequency.. 5599.87 BogoMIPS (lpj=11199740)
[    0.004045] Security Framework initialized
[    0.004055] SELinux:  Disabled at boot.
[    0.004076] AppArmor: AppArmor initialized
[    0.004846] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.007682] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.009046] Mount-cache hash table entries: 256
[    0.009315] Initializing cgroup subsys ns
[    0.009321] Initializing cgroup subsys cpuacct
[    0.009324] Initializing cgroup subsys memory
[    0.009348] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.009352] CPU: L2 cache: 1024K
[    0.009356] CPU 0/0 -> Node 0
[    0.009358] CPU: Physical Processor ID: 0
[    0.009360] CPU: Processor Core ID: 0
[    0.009376] CPU0: Thermal monitoring enabled (TM1)
[    0.009380] using mwait in idle threads.
[    0.011861] ACPI: Core revision 20080609
[    0.014090] ACPI: Checking initramfs for custom DSDT
[    0.391011] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.430709] CPU0:               Intel(R) Pentium(R) D CPU 2.80GHz stepping 07
[    0.430715] Using local APIC timer interrupts.
[    0.432029] APIC timer calibration result 12499730
[    0.432032] Detected 12.499 MHz APIC timer.
[    0.432227] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5599.94 BogoMIPS (lpj=11199887)
[    0.004000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.004000] CPU: L2 cache: 1024K
[    0.004000] CPU 1/1 -> Node 0
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] CPU1: Thermal monitoring enabled (TM1)
[    0.520442] CPU1:               Intel(R) Pentium(R) D CPU 2.80GHz stepping 07
[    0.520478] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.524063] Brought up 2 CPUs
[    0.524067] Total of 2 processors activated (11199.81 BogoMIPS).
[    0.524117] CPU0 attaching sched-domain:
[    0.524121]  domain 0: span 0-1 level CPU
[    0.524124]   groups: 0 1
[    0.524129]   domain 1: span 0-1 level NODE
[    0.524132]    groups: 0-1
[    0.524139] CPU1 attaching sched-domain:
[    0.524141]  domain 0: span 0-1 level CPU
[    0.524144]   groups: 1 0
[    0.524148]   domain 1: span 0-1 level NODE
[    0.524151]    groups: 0-1
[    0.524251] net_namespace: 1552 bytes
[    0.524251] Booting paravirtualized kernel on bare hardware
[    0.524357] Time: 12:27:41  Date: 05/10/09
[    0.524406] NET: Registered protocol family 16
[    0.524434] ACPI: bus type pci registered
[    0.524434] PCI: Found Intel Corporation 945G/GZ/P/PL Express Memory Controller Hub without MMCONFIG support.
[    0.524434] PCI: Using configuration type 1 for base access
[    0.528464] ACPI: EC: Look up EC in DSDT
[    0.533202] ACPI: Interpreter enabled
[    0.533206] ACPI: (supports S0 S1 S3 S4 S5)
[    0.533233] ACPI: Using IOAPIC for interrupt routing
[    0.540674] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.540674] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.540674] pci 0000:00:01.0: PME# disabled
[    0.540674] PCI: 0000:00:1b.0 reg 10 64bit mmio: [b3100000, b3103fff]
[    0.540674] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.540674] pci 0000:00:1b.0: PME# disabled
[    0.540674] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.540674] pci 0000:00:1c.0: PME# disabled
[    0.540674] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.540674] pci 0000:00:1c.2: PME# disabled
[    0.540674] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.540674] pci 0000:00:1c.3: PME# disabled
[    0.540674] PCI: 0000:00:1d.0 reg 20 io port: [3080, 309f]
[    0.540674] PCI: 0000:00:1d.1 reg 20 io port: [3060, 307f]
[    0.540674] PCI: 0000:00:1d.2 reg 20 io port: [3040, 305f]
[    0.540674] PCI: 0000:00:1d.3 reg 20 io port: [3020, 303f]
[    0.540683] PCI: 0000:00:1d.7 reg 10 32bit mmio: [b3104000, b31043ff]
[    0.540733] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.540739] pci 0000:00:1d.7: PME# disabled
[    0.540867] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.540874] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[    0.540879] pci 0000:00:1f.0: quirk: region 0500-053f claimed by ICH6 GPIO
[    0.540905] PCI: 0000:00:1f.1 reg 10 io port: [0, 7]
[    0.540912] PCI: 0000:00:1f.1 reg 14 io port: [0, 3]
[    0.540920] PCI: 0000:00:1f.1 reg 18 io port: [0, 7]
[    0.540927] PCI: 0000:00:1f.1 reg 1c io port: [0, 3]
[    0.540934] PCI: 0000:00:1f.1 reg 20 io port: [30b0, 30bf]
[    0.540978] PCI: 0000:00:1f.2 reg 10 io port: [30c8, 30cf]
[    0.540985] PCI: 0000:00:1f.2 reg 14 io port: [30e4, 30e7]
[    0.540992] PCI: 0000:00:1f.2 reg 18 io port: [30c0, 30c7]
[    0.540999] PCI: 0000:00:1f.2 reg 1c io port: [30e0, 30e3]
[    0.541005] PCI: 0000:00:1f.2 reg 20 io port: [30a0, 30af]
[    0.541029] pci 0000:00:1f.2: PME# supported from D3hot
[    0.541034] pci 0000:00:1f.2: PME# disabled
[    0.541079] PCI: 0000:00:1f.3 reg 20 io port: [3000, 301f]
[    0.541145] PCI: 0000:01:00.0 reg 10 32bit mmio: [b2000000, b2ffffff]
[    0.541152] PCI: 0000:01:00.0 reg 14 32bit mmio: [a0000000, afffffff]
[    0.541167] PCI: 0000:01:00.0 reg 1c 64bit mmio: [b0000000, b1ffffff]
[    0.541174] PCI: 0000:01:00.0 reg 24 io port: [2000, 207f]
[    0.541181] PCI: 0000:01:00.0 reg 30 32bit mmio: [fffe0000, ffffffff]
[    0.541234] PCI: bridge 0000:00:01.0 io port: [2000, 2fff]
[    0.541238] PCI: bridge 0000:00:01.0 32bit mmio: [b0000000, b2ffffff]
[    0.541244] PCI: bridge 0000:00:01.0 64bit mmio pref: [a0000000, afffffff]
[    0.541292] PCI: bridge 0000:00:1c.0 32bit mmio: [b3200000, b32fffff]
[    0.541344] PCI: bridge 0000:00:1c.2 32bit mmio: [b3300000, b33fffff]
[    0.541395] PCI: bridge 0000:00:1c.3 32bit mmio: [b3400000, b34fffff]
[    0.541426] PCI: 0000:05:00.0 reg 10 32bit mmio: [b3003000, b30031ff]
[    0.541460] PCI: 0000:05:00.0 reg 30 32bit mmio: [ffff0000, ffffffff]
[    0.541487] PCI: 0000:05:01.0 reg 10 32bit mmio: [b3000000, b3001fff]
[    0.541563] PCI: 0000:05:08.0 reg 10 32bit mmio: [b3002000, b3002fff]
[    0.541571] PCI: 0000:05:08.0 reg 14 io port: [1000, 103f]
[    0.541613] pci 0000:05:08.0: supports D1
[    0.541615] pci 0000:05:08.0: supports D2
[    0.541618] pci 0000:05:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.541625] pci 0000:05:08.0: PME# disabled
[    0.541660] pci 0000:00:1e.0: transparent bridge
[    0.541664] PCI: bridge 0000:00:1e.0 io port: [1000, 1fff]
[    0.541669] PCI: bridge 0000:00:1e.0 32bit mmio: [b3000000, b30fffff]
[    0.541705] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.542269] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[    0.542875] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.543078] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[    0.544189] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[    0.548262] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.548396] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.548581] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    0.548764] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.548946] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11 12)
[    0.549136] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11 12)
[    0.549320] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 *9 10 11 12)
[    0.549502] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 *10 11 12)
[    0.549604] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.549604] pnp: PnP ACPI init
[    0.549604] ACPI: bus type pnp registered
[    0.556368] pnp: PnP ACPI: found 13 devices
[    0.556368] ACPI: ACPI bus type pnp unregistered
[    0.556368] PCI: Using ACPI for IRQ routing
[    0.588048] NET: Registered protocol family 8
[    0.588051] NET: Registered protocol family 20
[    0.588074] NetLabel: Initializing
[    0.588074] NetLabel:  domain hash size = 128
[    0.588074] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.588091] NetLabel:  unlabeled traffic allowed by default
[    0.588117] PCI-GART: No AMD northbridge found.
[    0.588206] hpet clockevent registered
[    0.588211] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.588218] hpet0: 3 64-bit timers, 14318180 Hz
[    0.593535] tracer: 1286 pages allocated for 65536 entries of 80 bytes
[    0.593539]    actual entries 65586
[    0.593672] AppArmor: AppArmor Filesystem Enabled
[    0.593696] ACPI: RTC can wake from S4
[    0.608061] system 00:01: iomem range 0xf0000000-0xf3ffffff has been reserved
[    0.608066] system 00:01: iomem range 0xfed13000-0xfed13fff has been reserved
[    0.608069] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.608073] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.608076] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.608080] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.608083] system 00:01: iomem range 0xfed20000-0xfed9ffff has been reserved
[    0.608086] system 00:01: iomem range 0xc0000-0xdffff has been reserved
[    0.608090] system 00:01: iomem range 0xe0000-0xfffff could not be reserved
[    0.608105] system 00:06: ioport range 0x500-0x53f has been reserved
[    0.608115] system 00:06: ioport range 0x400-0x47f has been reserved
[    0.608118] system 00:06: ioport range 0x680-0x6ff has been reserved
[    0.613642] pci 0000:01:00.0: BAR 6: can't allocate mem resource [0xb0000000-0xafffffff]
[    0.613648] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.613652] pci 0000:00:01.0:   IO window: 0x2000-0x2fff
[    0.613658] pci 0000:00:01.0:   MEM window: 0xb0000000-0xb2ffffff
[    0.613662] pci 0000:00:01.0:   PREFETCH window: 0x000000a0000000-0x000000afffffff
[    0.613668] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.613670] pci 0000:00:1c.0:   IO window: disabled
[    0.613676] pci 0000:00:1c.0:   MEM window: 0xb3200000-0xb32fffff
[    0.613681] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.613688] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:03
[    0.613690] pci 0000:00:1c.2:   IO window: disabled
[    0.613695] pci 0000:00:1c.2:   MEM window: 0xb3300000-0xb33fffff
[    0.613700] pci 0000:00:1c.2:   PREFETCH window: disabled
[    0.613707] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:04
[    0.613709] pci 0000:00:1c.3:   IO window: disabled
[    0.613714] pci 0000:00:1c.3:   MEM window: 0xb3400000-0xb34fffff
[    0.613719] pci 0000:00:1c.3:   PREFETCH window: disabled
[    0.613726] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.613730] pci 0000:00:1e.0:   IO window: 0x1000-0x1fff
[    0.613736] pci 0000:00:1e.0:   MEM window: 0xb3000000-0xb30fffff
[    0.613740] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.613761] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.613766] pci 0000:00:01.0: setting latency timer to 64
[    0.613777] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.613782] pci 0000:00:1c.0: setting latency timer to 64
[    0.613792] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.613797] pci 0000:00:1c.2: setting latency timer to 64
[    0.613807] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.613812] pci 0000:00:1c.3: setting latency timer to 64
[    0.613820] pci 0000:00:1e.0: setting latency timer to 64
[    0.613825] bus: 00 index 0 io port: [0, ffff]
[    0.613827] bus: 00 index 1 mmio: [0, ffffffffffffffff]
[    0.613830] bus: 01 index 0 io port: [2000, 2fff]
[    0.613833] bus: 01 index 1 mmio: [b0000000, b2ffffff]
[    0.613835] bus: 01 index 2 mmio: [a0000000, afffffff]
[    0.613838] bus: 01 index 3 mmio: [0, 0]
[    0.613840] bus: 02 index 0 mmio: [0, 0]
[    0.613842] bus: 02 index 1 mmio: [b3200000, b32fffff]
[    0.613844] bus: 02 index 2 mmio: [0, 0]
[    0.613846] bus: 02 index 3 mmio: [0, 0]
[    0.613849] bus: 03 index 0 mmio: [0, 0]
[    0.613851] bus: 03 index 1 mmio: [b3300000, b33fffff]
[    0.613853] bus: 03 index 2 mmio: [0, 0]
[    0.613855] bus: 03 index 3 mmio: [0, 0]
[    0.613858] bus: 04 index 0 mmio: [0, 0]
[    0.613860] bus: 04 index 1 mmio: [b3400000, b34fffff]
[    0.613862] bus: 04 index 2 mmio: [0, 0]
[    0.613864] bus: 04 index 3 mmio: [0, 0]
[    0.613867] bus: 05 index 0 io port: [1000, 1fff]
[    0.613869] bus: 05 index 1 mmio: [b3000000, b30fffff]
[    0.613871] bus: 05 index 2 mmio: [0, 0]
[    0.613873] bus: 05 index 3 io port: [0, ffff]
[    0.613876] bus: 05 index 4 mmio: [0, ffffffffffffffff]
[    0.613893] NET: Registered protocol family 2
[    0.652286] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.654428] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.659873] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.660524] TCP: Hash tables configured (established 524288 bind 65536)
[    0.660530] TCP reno registered
[    0.672178] NET: Registered protocol family 1
[    0.672340] checking if image is initramfs... it is
[    1.088517] Switched to high resolution mode on CPU 1
[    1.092033] Switched to high resolution mode on CPU 0
[    1.451263] Freeing initrd memory: 8427k freed
[    1.458562] audit: initializing netlink socket (disabled)
[    1.458593] type=2000 audit(1241958461.456:1): initialized
[    1.464653] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.468387] VFS: Disk quotas dquot_6.5.1
[    1.468575] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.468732] msgmni has been set to 5021
[    1.468902] io scheduler noop registered
[    1.468905] io scheduler anticipatory registered
[    1.468908] io scheduler deadline registered
[    1.469082] io scheduler cfq registered (default)
[    1.469312] pci 0000:01:00.0: Boot video device
[    1.469329] pci 0000:05:08.0: Firmware left e100 interrupts enabled; disabling
[    1.469483] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.469523] pcieport-driver 0000:00:01.0: found MSI capability
[    1.469559] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.469683] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.469718] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.469757] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.469820] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.469939] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.469974] pcieport-driver 0000:00:1c.2: found MSI capability
[    1.470012] pci_express 0000:00:1c.2:pcie00: allocate port service
[    1.470081] pci_express 0000:00:1c.2:pcie02: allocate port service
[    1.470204] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.470240] pcieport-driver 0000:00:1c.3: found MSI capability
[    1.470277] pci_express 0000:00:1c.3:pcie00: allocate port service
[    1.470341] pci_express 0000:00:1c.3:pcie02: allocate port service
[    1.520471] Linux agpgart interface v0.103
[    1.520478] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.520662] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.521614] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.524245] brd: module loaded
[    1.524345] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.524591] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.527550] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.527559] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.552679] mice: PS/2 mouse device common for all mice
[    1.552867] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.552896] rtc0: alarms up to one month, hpet irqs
[    1.552962] cpuidle: using governor ladder
[    1.552966] cpuidle: using governor menu
[    1.553446] TCP cubic registered
[    1.553749] registered taskstats version 1
[    1.553902]   Magic number: 9:940:480
[    1.554047] rtc_cmos 00:03: setting system clock to 2009-05-10 12:27:42 UTC (1241958462)
[    1.554051] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.554054] EDD information not available.
[    1.554111] Freeing unused kernel memory: 536k freed
[    1.554418] Write protecting the kernel read-only data: 4348k
[    1.577913] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.727505] fuse init (API version 7.9)
[    1.852769] processor ACPI0007:00: registered as cooling_device0
[    1.852876] processor ACPI0007:01: registered as cooling_device1
[    2.361807] usbcore: registered new interface driver usbfs
[    2.361845] usbcore: registered new interface driver hub
[    2.372836] usbcore: registered new device driver usb
[    2.378229] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[    2.378233] e100: Copyright(c) 1999-2006 Intel Corporation
[    2.378299] e100 0000:05:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.403363] e100 0000:05:08.0: PME# disabled
[    2.410585] e100: eth0: e100_probe: addr 0xb3002000, irq 20, MAC addr 00:16:76:31:52:fa
[    2.411923] b43-pci-bridge 0000:05:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    2.414099] No dock devices found.
[    2.429269] SCSI subsystem initialized
[    2.447393] libata version 3.00 loaded.
[    2.481757] USB Universal Host Controller Interface driver v3.0
[    2.488690] ssb: Sonics Silicon Backplane found on PCI device 0000:05:01.0
[    2.488803] ata_piix 0000:00:1f.1: version 2.12
[    2.488819] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.488867] ata_piix 0000:00:1f.1: setting latency timer to 64
[    2.489437] scsi0 : ata_piix
[    2.489581] scsi1 : ata_piix
[    2.490628] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x30b0 irq 14
[    2.490632] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x30b8 irq 15
[    2.829086] ata1.00: ATAPI: SONY    DVD RW DRU-710A, BY03, max UDMA/66
[    2.829104] ata1.01: ATAPI: LITE-ON LTR-48126S, 2QS5, max UDMA/33
[    2.844986] ata1.00: configured for UDMA/66
[    2.860842] ata1.01: configured for UDMA/33
[    2.860900] ata2: port disabled. ignoring.
[    2.860955] isa bounce pool size: 16 pages
[    2.861815] scsi 0:0:0:0: CD-ROM            SONY     DVD RW DRU-710A  BY03 PQ: 0 ANSI: 5
[    2.862408] scsi 0:0:1:0: CD-ROM            LITE-ON  LTR-48126S       2QS5 PQ: 0 ANSI: 5
[    2.862563] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.862569] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    2.862618] ata_piix 0000:00:1f.2: setting latency timer to 64
[    2.864143] scsi2 : ata_piix
[    2.864283] scsi3 : ata_piix
[    2.864477] ata3: SATA max UDMA/133 cmd 0x30c8 ctl 0x30e4 bmdma 0x30a0 irq 19
[    2.864482] ata4: SATA max UDMA/133 cmd 0x30c0 ctl 0x30e0 bmdma 0x30a8 irq 19
[    3.036992] ata3.00: ATA-6: ST380817AS, 9.01, max UDMA/133
[    3.036998] ata3.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.037157] ata3.01: ATA-6: WDC WD800JD-23JNC0, 06.01C06, max UDMA/133
[    3.037161] ata3.01: 156312576 sectors, multi 16: LBA 
[    3.052961] ata3.00: configured for UDMA/133
[    3.061029] ata3.01: configured for UDMA/133
[    3.224316] ata4.00: ATA-7: WDC WD800JD-22LSA0, 06.01D06, max UDMA/133
[    3.224322] ata4.00: 156301488 sectors, multi 16: LBA48 
[    3.232323] ata4.00: configured for UDMA/133
[    3.232477] scsi 2:0:0:0: Direct-Access     ATA      ST380817AS       9.01 PQ: 0 ANSI: 5
[    3.232693] scsi 2:0:1:0: Direct-Access     ATA      WDC WD800JD-23JN 06.0 PQ: 0 ANSI: 5
[    3.232857] scsi 3:0:0:0: Direct-Access     ATA      WDC WD800JD-22LS 06.0 PQ: 0 ANSI: 5
[    3.237739] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.237752] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.237757] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.237829] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.237868] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00003080
[    3.238060] usb usb1: configuration #1 chosen from 1 choice
[    3.238099] hub 1-0:1.0: USB hub found
[    3.238110] hub 1-0:1.0: 2 ports detected
[    3.342324] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.342336] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.342341] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.342389] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.342419] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00003060
[    3.342580] usb usb2: configuration #1 chosen from 1 choice
[    3.342619] hub 2-0:1.0: USB hub found
[    3.342629] hub 2-0:1.0: 2 ports detected
[    3.549415] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.549426] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.549430] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.549472] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.549512] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00003040
[    3.549648] usb usb3: configuration #1 chosen from 1 choice
[    3.549684] hub 3-0:1.0: USB hub found
[    3.549695] hub 3-0:1.0: 2 ports detected
[    3.653456] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    3.653465] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    3.653469] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.653516] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.653555] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00003020
[    3.653687] usb usb4: configuration #1 chosen from 1 choice
[    3.653724] hub 4-0:1.0: USB hub found
[    3.653734] hub 4-0:1.0: 2 ports detected
[    3.660519] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    3.756258] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.756276] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.756282] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.756340] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.760233] ehci_hcd 0000:00:1d.7: debug port 1
[    3.760240] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    3.760251] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xb3104000
[    3.788016] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.788968] usb usb5: configuration #1 chosen from 1 choice
[    3.789676] hub 5-0:1.0: USB hub found
[    3.789688] hub 5-0:1.0: 8 ports detected
[    4.012151] scsi 0:0:0:0: Attached scsi generic sg0 type 5
[    4.012203] scsi 0:0:1:0: Attached scsi generic sg1 type 5
[    4.012253] scsi 2:0:0:0: Attached scsi generic sg2 type 0
[    4.012303] scsi 2:0:1:0: Attached scsi generic sg3 type 0
[    4.012350] scsi 3:0:0:0: Attached scsi generic sg4 type 0
[    4.085053] Driver 'sr' needs updating - please use bus_type methods
[    4.090041] Driver 'sd' needs updating - please use bus_type methods
[    4.092703] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    4.092709] Uniform CD-ROM driver Revision: 3.20
[    4.092845] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    4.093947] sr1: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    4.094037] sr 0:0:1:0: Attached scsi CD-ROM sr1
[    4.094181] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    4.094212] sd 2:0:0:0: [sda] Write Protect is off
[    4.094216] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.094269] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.094370] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    4.094399] sd 2:0:0:0: [sda] Write Protect is off
[    4.094403] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.094456] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.094462]  sda: sda1
[    4.101926] sd 2:0:0:0: [sda] Attached SCSI disk
[    4.102068] sd 2:0:1:0: [sdb] 156312576 512-byte hardware sectors (80032 MB)
[    4.102102] sd 2:0:1:0: [sdb] Write Protect is off
[    4.102106] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    4.102164] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.102261] sd 2:0:1:0: [sdb] 156312576 512-byte hardware sectors (80032 MB)
[    4.102292] sd 2:0:1:0: [sdb] Write Protect is off
[    4.102296] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    4.102352] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.102359]  sdb: sdb1 sdb2 < sdb5 >
[    4.122949] sd 2:0:1:0: [sdb] Attached SCSI disk
[    4.123071] sd 3:0:0:0: [sdc] 156301488 512-byte hardware sectors (80026 MB)
[    4.123103] sd 3:0:0:0: [sdc] Write Protect is off
[    4.123107] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    4.123281] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.123374] sd 3:0:0:0: [sdc] 156301488 512-byte hardware sectors (80026 MB)
[    4.123403] sd 3:0:0:0: [sdc] Write Protect is off
[    4.123407] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    4.123460] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.123466]  sdc: sdc1
[    4.133939] sd 3:0:0:0: [sdc] Attached SCSI disk
[    4.188027] usb 2-1: device not accepting address 2, error -71
[    4.244057] hub 2-0:1.0: unable to enumerate USB device on port 1
[    4.616017] usb 2-1: new low speed USB device using uhci_hcd and address 4
[    4.796408] usb 2-1: configuration #1 chosen from 1 choice
[    4.823275] usbcore: registered new interface driver hiddev
[    4.835758] input: Kensington      Kensington USB/PS2 Orbit as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.0/input/input2
[    4.852202] input,hidraw0: USB HID v1.10 Mouse [Kensington      Kensington USB/PS2 Orbit] on usb-0000:00:1d.1-1
[    4.852233] usbcore: registered new interface driver usbhid
[    4.852237] usbhid: v2.6:USB HID core driver
[    7.460708] PM: Starting manual resume from disk
[    7.460714] PM: Resume from partition 8:17
[    7.460717] PM: Checking hibernation image.
[    7.460896] PM: Resume from disk failed.
[    7.517730] kjournald starting.  Commit interval 5 seconds
[    7.517749] EXT3-fs: mounted filesystem with ordered data mode.
[   12.917059] udevd version 124 started
[   13.341865] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   13.400608] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.573509] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   13.592047] ACPI: Power Button (FF) [PWRF]
[   13.592155] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   13.624059] ACPI: Sleep Button (CM) [SLPB]
[   13.661881] iTCO_vendor_support: vendor-support=0
[   13.741875] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   13.741981] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0460)
[   13.742104] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   13.789837] intel_rng: Firmware space is locked read-only. If you can't or
[   13.789840] intel_rng: don't want to disable this in firmware setup, and if
[   13.789842] intel_rng: you are certain that your system has a functional
[   13.789843] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   13.897346] parport_pc 00:08: reported by Plug and Play ACPI
[   13.897409] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   14.321444] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   14.321488] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.495119] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   14.622109] b43-phy0: Broadcom 4318 WLAN found
[   14.672032] logips2pp: Detected unknown logitech mouse model 127
[   14.713708] phy0: Selected rate control algorithm 'pid'
[   14.967992] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
[   15.137964] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input6
[   16.966538] lp0: using parport0 (interrupt-driven).
[   17.179384] Adding 497972k swap on /dev/sdb1.  Priority:-1 extents:1 across:497972k
[   17.751177] EXT3 FS on sdb5, internal journal
[   18.876544] type=1505 audit(1241976480.140:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4287
[   19.065190] type=1505 audit(1241976480.328:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4292
[   19.065400] type=1505 audit(1241976480.328:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4292
[   19.233355] ip_tables: (C) 2000-2006 Netfilter Core Team
[   19.995418] ACPI: WMI: Mapper loaded
[   21.080947] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   21.251557] ppdev: user-space parallel port driver
[   22.678876] Bluetooth: Core ver 2.13
[   22.681587] NET: Registered protocol family 31
[   22.681594] Bluetooth: HCI device and connection manager initialized
[   22.681598] Bluetooth: HCI socket layer initialized
[   22.693849] Bluetooth: L2CAP ver 2.11
[   22.693857] Bluetooth: L2CAP socket layer initialized
[   22.706788] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.706796] Bluetooth: BNEP filters: protocol multicast
[   22.725999] Bridge firewalling registered
[   22.727159] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   22.738444] Bluetooth: SCO (Voice Link) ver 0.6
[   22.738452] Bluetooth: SCO socket layer initialized
[   22.850344] Bluetooth: RFCOMM socket layer initialized
[   22.851611] Bluetooth: RFCOMM TTY layer initialized
[   22.851618] Bluetooth: RFCOMM ver 1.10
[   27.061883] input: b43-phy0 as /devices/virtual/input/input7
[   27.180539] firmware: requesting b43/ucode5.fw
[   27.263711] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   27.263725] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[   27.345517] input: b43-phy0 as /devices/virtual/input/input8
[   27.452038] firmware: requesting b43/ucode5.fw
[   27.455886] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   27.455896] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[   27.704927] NET: Registered protocol family 17
[   41.685565] UDF-fs: No VRS found
[   41.703324] ISO 9660 Extensions: Microsoft Joliet Level 3
[   41.705302] ISOFS: changing to secondary root
[  114.244338] type=1503 audit(1241976575.508:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/5841/net/" pid=5841 profile="/usr/sbin/cupsd"
[  114.315282] NET: Registered protocol family 10
[  114.316524] lo: Disabled Privacy Extensions
[  114.317350] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  114.319763] type=1503 audit(1241976575.580:6): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=5841 profile="/usr/sbin/cupsd"
[  114.319778] type=1503 audit(1241976575.580:7): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=5841 profile="/usr/sbin/cupsd"
[  114.319786] type=1503 audit(1241976575.580:8): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=5841 profile="/usr/sbin/cupsd"
[  114.319794] type=1503 audit(1241976575.580:9): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=5841 profile="/usr/sbin/cupsd"
[  114.319801] type=1503 audit(1241976575.580:10): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=5841 profile="/usr/sbin/cupsd"
[  114.319808] type=1503 audit(1241976575.580:11): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=5841 profile="/usr/sbin/cupsd"
[  114.319815] type=1503 audit(1241976575.580:12): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=5841 profile="/usr/sbin/cupsd"
[  114.319823] type=1503 audit(1241976575.580:13): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=5841 profile="/usr/sbin/cupsd"
[  114.319901] type=1503 audit(1241976575.580:14): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/proc/5841/net/dev" pid=5841 profile="/usr/sbin/cupsd"
[  114.560299] ppdev0: registered pardevice
[  114.608339] ppdev0: unregistered pardevice
[  114.668252] ppdev0: registered pardevice
[  114.716046] ppdev0: unregistered pardevice
[  116.208588] ppdev0: registered pardevice
[  116.256206] ppdev0: unregistered pardevice
kyle@kyle-desktop:~$ clear

kyle@kyle-desktop:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-generic (buildd@yellow) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu10) ) #1 SMP Fri Oct 24 06:40:41 UTC 2008 (Ubuntu 2.6.27-7.14-generic)
[    0.000000] Command line: root=UUID=21222dbe-0b84-4408-b939-a3fea2063593 ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000009f023000 (usable)
[    0.000000]  BIOS-e820: 000000009f023000 - 000000009f071000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000009f071000 - 000000009fea9000 (usable)
[    0.000000]  BIOS-e820: 000000009fea9000 - 000000009fee9000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000009fee9000 - 000000009feed000 (usable)
[    0.000000]  BIOS-e820: 000000009feed000 - 000000009feff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000009feff000 - 000000009ff00000 (usable)
[    0.000000] last_pfn = 0x9ff00 max_arch_pfn = 0x3ffffffff
[    0.000000] init_memory_mapping
[    0.000000]  0000000000 - 009fe00000 page 2M
[    0.000000]  009fe00000 - 009ff00000 page 4k
[    0.000000] kernel direct mapping tables up to 9ff00000 @ 8000-d000
[    0.000000] last_map_addr: 9ff00000 end: 9ff00000
[    0.000000] RAMDISK: 377b5000 - 37fefd74
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP 000FE020, 0014 (r0 INTEL )
[    0.000000] ACPI: RSDT 9FEFDE48, 0038 (r1 INTEL  D945GTP       9B7 MSFT  1000013)
[    0.000000] ACPI: FACP 9FEFCF10, 0074 (r1 INTEL  D945GTP       9B7 MSFT  1000013)
[    0.000000] ACPI: DSDT 9FEF8010, 3FBC (r1 INTEL  D945GTP       9B7 MSFT  1000013)
[    0.000000] ACPI: FACS 9FEE5C40, 0040
[    0.000000] ACPI: APIC 9FEFCE10, 0078 (r1 INTEL  D945GTP       9B7 MSFT  1000013)
[    0.000000] ACPI: WDDT 9FEF7F90, 0040 (r1 INTEL  D945GTP       9B7 MSFT  1000013)
[    0.000000] ACPI: MCFG 9FEF7F10, 003C (r1 INTEL  D945GTP       9B7 MSFT  1000013)
[    0.000000] ACPI: ASF! 9FEFCD10, 00A6 (r32 INTEL  D945GTP       9B7 MSFT  1000013)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000009ff00000
[    0.000000] Bootmem setup node 0 0000000000000000-000000009ff00000
[    0.000000]   NODE_DATA [0000000000001000 - 0000000000005fff]
[    0.000000]   bootmap [000000000000b000 -  000000000001efdf] pages 14
[    0.000000] (6 early reservations) ==> bootmem [0000000000 - 009ff00000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 00008b8f9c]    TEXT DATA BSS ==> [0000200000 - 00008b8f9c]
[    0.000000]   #3 [00377b5000 - 0037fefd74]          RAMDISK ==> [00377b5000 - 0037fefd74]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [0000008000 - 000000b000]          PGTABLE ==> [0000008000 - 000000b000]
[    0.000000] found SMP MP-table at [ffff8800000fe680] 000fe680
[    0.000000]  [ffffe20000000000-ffffe200027fffff] PMD -> [ffff880001200000-ffff8800039fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[5] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0009f023
[    0.000000]     0: 0x0009f071 -> 0x0009fea9
[    0.000000]     0: 0x0009fee9 -> 0x0009feed
[    0.000000]     0: 0x0009feff -> 0x0009ff00
[    0.000000] On node 0 totalpages: 654847
[    0.000000]   DMA zone: 2111 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 640676 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 000000009f023000 - 000000009f071000
[    0.000000] PM: Registered nosave memory: 000000009fea9000 - 000000009fee9000
[    0.000000] PM: Registered nosave memory: 000000009feed000 - 000000009feff000
[    0.000000] Allocating PCI resources starting at a0000000 (gap: 9ff00000:60100000)
[    0.000000] PERCPU: Allocating 64928 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 642787
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=21222dbe-0b84-4408-b939-a3fea2063593 ro quiet splash 
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PMTIMER calibration value
[    0.000000] Detected 2799.935 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Calgary: detecting Calgary via BIOS EBDA area
[    0.004000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.004000] Memory: 2562636k/2620416k available (3112k kernel code, 56752k reserved, 1575k data, 536k init)
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004013] Calibrating delay loop (skipped), value calculated using timer frequency.. 5599.87 BogoMIPS (lpj=11199740)
[    0.004045] Security Framework initialized
[    0.004055] SELinux:  Disabled at boot.
[    0.004076] AppArmor: AppArmor initialized
[    0.004846] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.007682] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.009046] Mount-cache hash table entries: 256
[    0.009315] Initializing cgroup subsys ns
[    0.009321] Initializing cgroup subsys cpuacct
[    0.009324] Initializing cgroup subsys memory
[    0.009348] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.009352] CPU: L2 cache: 1024K
[    0.009356] CPU 0/0 -> Node 0
[    0.009358] CPU: Physical Processor ID: 0
[    0.009360] CPU: Processor Core ID: 0
[    0.009376] CPU0: Thermal monitoring enabled (TM1)
[    0.009380] using mwait in idle threads.
[    0.011861] ACPI: Core revision 20080609
[    0.014090] ACPI: Checking initramfs for custom DSDT
[    0.391011] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.430709] CPU0:               Intel(R) Pentium(R) D CPU 2.80GHz stepping 07
[    0.430715] Using local APIC timer interrupts.
[    0.432029] APIC timer calibration result 12499730
[    0.432032] Detected 12.499 MHz APIC timer.
[    0.432227] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5599.94 BogoMIPS (lpj=11199887)
[    0.004000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.004000] CPU: L2 cache: 1024K
[    0.004000] CPU 1/1 -> Node 0
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] CPU1: Thermal monitoring enabled (TM1)
[    0.520442] CPU1:               Intel(R) Pentium(R) D CPU 2.80GHz stepping 07
[    0.520478] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.524063] Brought up 2 CPUs
[    0.524067] Total of 2 processors activated (11199.81 BogoMIPS).
[    0.524117] CPU0 attaching sched-domain:
[    0.524121]  domain 0: span 0-1 level CPU
[    0.524124]   groups: 0 1
[    0.524129]   domain 1: span 0-1 level NODE
[    0.524132]    groups: 0-1
[    0.524139] CPU1 attaching sched-domain:
[    0.524141]  domain 0: span 0-1 level CPU
[    0.524144]   groups: 1 0
[    0.524148]   domain 1: span 0-1 level NODE
[    0.524151]    groups: 0-1
[    0.524251] net_namespace: 1552 bytes
[    0.524251] Booting paravirtualized kernel on bare hardware
[    0.524357] Time: 12:27:41  Date: 05/10/09
[    0.524406] NET: Registered protocol family 16
[    0.524434] ACPI: bus type pci registered
[    0.524434] PCI: Found Intel Corporation 945G/GZ/P/PL Express Memory Controller Hub without MMCONFIG support.
[    0.524434] PCI: Using configuration type 1 for base access
[    0.528464] ACPI: EC: Look up EC in DSDT
[    0.533202] ACPI: Interpreter enabled
[    0.533206] ACPI: (supports S0 S1 S3 S4 S5)
[    0.533233] ACPI: Using IOAPIC for interrupt routing
[    0.540674] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.540674] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.540674] pci 0000:00:01.0: PME# disabled
[    0.540674] PCI: 0000:00:1b.0 reg 10 64bit mmio: [b3100000, b3103fff]
[    0.540674] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.540674] pci 0000:00:1b.0: PME# disabled
[    0.540674] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.540674] pci 0000:00:1c.0: PME# disabled
[    0.540674] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.540674] pci 0000:00:1c.2: PME# disabled
[    0.540674] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.540674] pci 0000:00:1c.3: PME# disabled
[    0.540674] PCI: 0000:00:1d.0 reg 20 io port: [3080, 309f]
[    0.540674] PCI: 0000:00:1d.1 reg 20 io port: [3060, 307f]
[    0.540674] PCI: 0000:00:1d.2 reg 20 io port: [3040, 305f]
[    0.540674] PCI: 0000:00:1d.3 reg 20 io port: [3020, 303f]
[    0.540683] PCI: 0000:00:1d.7 reg 10 32bit mmio: [b3104000, b31043ff]
[    0.540733] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.540739] pci 0000:00:1d.7: PME# disabled
[    0.540867] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.540874] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[    0.540879] pci 0000:00:1f.0: quirk: region 0500-053f claimed by ICH6 GPIO
[    0.540905] PCI: 0000:00:1f.1 reg 10 io port: [0, 7]
[    0.540912] PCI: 0000:00:1f.1 reg 14 io port: [0, 3]
[    0.540920] PCI: 0000:00:1f.1 reg 18 io port: [0, 7]
[    0.540927] PCI: 0000:00:1f.1 reg 1c io port: [0, 3]
[    0.540934] PCI: 0000:00:1f.1 reg 20 io port: [30b0, 30bf]
[    0.540978] PCI: 0000:00:1f.2 reg 10 io port: [30c8, 30cf]
[    0.540985] PCI: 0000:00:1f.2 reg 14 io port: [30e4, 30e7]
[    0.540992] PCI: 0000:00:1f.2 reg 18 io port: [30c0, 30c7]
[    0.540999] PCI: 0000:00:1f.2 reg 1c io port: [30e0, 30e3]
[    0.541005] PCI: 0000:00:1f.2 reg 20 io port: [30a0, 30af]
[    0.541029] pci 0000:00:1f.2: PME# supported from D3hot
[    0.541034] pci 0000:00:1f.2: PME# disabled
[    0.541079] PCI: 0000:00:1f.3 reg 20 io port: [3000, 301f]
[    0.541145] PCI: 0000:01:00.0 reg 10 32bit mmio: [b2000000, b2ffffff]
[    0.541152] PCI: 0000:01:00.0 reg 14 32bit mmio: [a0000000, afffffff]
[    0.541167] PCI: 0000:01:00.0 reg 1c 64bit mmio: [b0000000, b1ffffff]
[    0.541174] PCI: 0000:01:00.0 reg 24 io port: [2000, 207f]
[    0.541181] PCI: 0000:01:00.0 reg 30 32bit mmio: [fffe0000, ffffffff]
[    0.541234] PCI: bridge 0000:00:01.0 io port: [2000, 2fff]
[    0.541238] PCI: bridge 0000:00:01.0 32bit mmio: [b0000000, b2ffffff]
[    0.541244] PCI: bridge 0000:00:01.0 64bit mmio pref: [a0000000, afffffff]
[    0.541292] PCI: bridge 0000:00:1c.0 32bit mmio: [b3200000, b32fffff]
[    0.541344] PCI: bridge 0000:00:1c.2 32bit mmio: [b3300000, b33fffff]
[    0.541395] PCI: bridge 0000:00:1c.3 32bit mmio: [b3400000, b34fffff]
[    0.541426] PCI: 0000:05:00.0 reg 10 32bit mmio: [b3003000, b30031ff]
[    0.541460] PCI: 0000:05:00.0 reg 30 32bit mmio: [ffff0000, ffffffff]
[    0.541487] PCI: 0000:05:01.0 reg 10 32bit mmio: [b3000000, b3001fff]
[    0.541563] PCI: 0000:05:08.0 reg 10 32bit mmio: [b3002000, b3002fff]
[    0.541571] PCI: 0000:05:08.0 reg 14 io port: [1000, 103f]
[    0.541613] pci 0000:05:08.0: supports D1
[    0.541615] pci 0000:05:08.0: supports D2
[    0.541618] pci 0000:05:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.541625] pci 0000:05:08.0: PME# disabled
[    0.541660] pci 0000:00:1e.0: transparent bridge
[    0.541664] PCI: bridge 0000:00:1e.0 io port: [1000, 1fff]
[    0.541669] PCI: bridge 0000:00:1e.0 32bit mmio: [b3000000, b30fffff]
[    0.541705] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.542269] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[    0.542875] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.543078] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[    0.544189] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[    0.548262] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.548396] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.548581] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    0.548764] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.548946] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11 12)
[    0.549136] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11 12)
[    0.549320] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 *9 10 11 12)
[    0.549502] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 *10 11 12)
[    0.549604] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.549604] pnp: PnP ACPI init
[    0.549604] ACPI: bus type pnp registered
[    0.556368] pnp: PnP ACPI: found 13 devices
[    0.556368] ACPI: ACPI bus type pnp unregistered
[    0.556368] PCI: Using ACPI for IRQ routing
[    0.588048] NET: Registered protocol family 8
[    0.588051] NET: Registered protocol family 20
[    0.588074] NetLabel: Initializing
[    0.588074] NetLabel:  domain hash size = 128
[    0.588074] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.588091] NetLabel:  unlabeled traffic allowed by default
[    0.588117] PCI-GART: No AMD northbridge found.
[    0.588206] hpet clockevent registered
[    0.588211] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.588218] hpet0: 3 64-bit timers, 14318180 Hz
[    0.593535] tracer: 1286 pages allocated for 65536 entries of 80 bytes
[    0.593539]    actual entries 65586
[    0.593672] AppArmor: AppArmor Filesystem Enabled
[    0.593696] ACPI: RTC can wake from S4
[    0.608061] system 00:01: iomem range 0xf0000000-0xf3ffffff has been reserved
[    0.608066] system 00:01: iomem range 0xfed13000-0xfed13fff has been reserved
[    0.608069] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.608073] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.608076] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.608080] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.608083] system 00:01: iomem range 0xfed20000-0xfed9ffff has been reserved
[    0.608086] system 00:01: iomem range 0xc0000-0xdffff has been reserved
[    0.608090] system 00:01: iomem range 0xe0000-0xfffff could not be reserved
[    0.608105] system 00:06: ioport range 0x500-0x53f has been reserved
[    0.608115] system 00:06: ioport range 0x400-0x47f has been reserved
[    0.608118] system 00:06: ioport range 0x680-0x6ff has been reserved
[    0.613642] pci 0000:01:00.0: BAR 6: can't allocate mem resource [0xb0000000-0xafffffff]
[    0.613648] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.613652] pci 0000:00:01.0:   IO window: 0x2000-0x2fff
[    0.613658] pci 0000:00:01.0:   MEM window: 0xb0000000-0xb2ffffff
[    0.613662] pci 0000:00:01.0:   PREFETCH window: 0x000000a0000000-0x000000afffffff
[    0.613668] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.613670] pci 0000:00:1c.0:   IO window: disabled
[    0.613676] pci 0000:00:1c.0:   MEM window: 0xb3200000-0xb32fffff
[    0.613681] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.613688] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:03
[    0.613690] pci 0000:00:1c.2:   IO window: disabled
[    0.613695] pci 0000:00:1c.2:   MEM window: 0xb3300000-0xb33fffff
[    0.613700] pci 0000:00:1c.2:   PREFETCH window: disabled
[    0.613707] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:04
[    0.613709] pci 0000:00:1c.3:   IO window: disabled
[    0.613714] pci 0000:00:1c.3:   MEM window: 0xb3400000-0xb34fffff
[    0.613719] pci 0000:00:1c.3:   PREFETCH window: disabled
[    0.613726] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.613730] pci 0000:00:1e.0:   IO window: 0x1000-0x1fff
[    0.613736] pci 0000:00:1e.0:   MEM window: 0xb3000000-0xb30fffff
[    0.613740] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.613761] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.613766] pci 0000:00:01.0: setting latency timer to 64
[    0.613777] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.613782] pci 0000:00:1c.0: setting latency timer to 64
[    0.613792] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.613797] pci 0000:00:1c.2: setting latency timer to 64
[    0.613807] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.613812] pci 0000:00:1c.3: setting latency timer to 64
[    0.613820] pci 0000:00:1e.0: setting latency timer to 64
[    0.613825] bus: 00 index 0 io port: [0, ffff]
[    0.613827] bus: 00 index 1 mmio: [0, ffffffffffffffff]
[    0.613830] bus: 01 index 0 io port: [2000, 2fff]
[    0.613833] bus: 01 index 1 mmio: [b0000000, b2ffffff]
[    0.613835] bus: 01 index 2 mmio: [a0000000, afffffff]
[    0.613838] bus: 01 index 3 mmio: [0, 0]
[    0.613840] bus: 02 index 0 mmio: [0, 0]
[    0.613842] bus: 02 index 1 mmio: [b3200000, b32fffff]
[    0.613844] bus: 02 index 2 mmio: [0, 0]
[    0.613846] bus: 02 index 3 mmio: [0, 0]
[    0.613849] bus: 03 index 0 mmio: [0, 0]
[    0.613851] bus: 03 index 1 mmio: [b3300000, b33fffff]
[    0.613853] bus: 03 index 2 mmio: [0, 0]
[    0.613855] bus: 03 index 3 mmio: [0, 0]
[    0.613858] bus: 04 index 0 mmio: [0, 0]
[    0.613860] bus: 04 index 1 mmio: [b3400000, b34fffff]
[    0.613862] bus: 04 index 2 mmio: [0, 0]
[    0.613864] bus: 04 index 3 mmio: [0, 0]
[    0.613867] bus: 05 index 0 io port: [1000, 1fff]
[    0.613869] bus: 05 index 1 mmio: [b3000000, b30fffff]
[    0.613871] bus: 05 index 2 mmio: [0, 0]
[    0.613873] bus: 05 index 3 io port: [0, ffff]
[    0.613876] bus: 05 index 4 mmio: [0, ffffffffffffffff]
[    0.613893] NET: Registered protocol family 2
[    0.652286] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.654428] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.659873] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.660524] TCP: Hash tables configured (established 524288 bind 65536)
[    0.660530] TCP reno registered
[    0.672178] NET: Registered protocol family 1
[    0.672340] checking if image is initramfs... it is
[    1.088517] Switched to high resolution mode on CPU 1
[    1.092033] Switched to high resolution mode on CPU 0
[    1.451263] Freeing initrd memory: 8427k freed
[    1.458562] audit: initializing netlink socket (disabled)
[    1.458593] type=2000 audit(1241958461.456:1): initialized
[    1.464653] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.468387] VFS: Disk quotas dquot_6.5.1
[    1.468575] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.468732] msgmni has been set to 5021
[    1.468902] io scheduler noop registered
[    1.468905] io scheduler anticipatory registered
[    1.468908] io scheduler deadline registered
[    1.469082] io scheduler cfq registered (default)
[    1.469312] pci 0000:01:00.0: Boot video device
[    1.469329] pci 0000:05:08.0: Firmware left e100 interrupts enabled; disabling
[    1.469483] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.469523] pcieport-driver 0000:00:01.0: found MSI capability
[    1.469559] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.469683] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.469718] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.469757] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.469820] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.469939] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.469974] pcieport-driver 0000:00:1c.2: found MSI capability
[    1.470012] pci_express 0000:00:1c.2:pcie00: allocate port service
[    1.470081] pci_express 0000:00:1c.2:pcie02: allocate port service
[    1.470204] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.470240] pcieport-driver 0000:00:1c.3: found MSI capability
[    1.470277] pci_express 0000:00:1c.3:pcie00: allocate port service
[    1.470341] pci_express 0000:00:1c.3:pcie02: allocate port service
[    1.520471] Linux agpgart interface v0.103
[    1.520478] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.520662] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.521614] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.524245] brd: module loaded
[    1.524345] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.524591] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.527550] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.527559] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.552679] mice: PS/2 mouse device common for all mice
[    1.552867] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.552896] rtc0: alarms up to one month, hpet irqs
[    1.552962] cpuidle: using governor ladder
[    1.552966] cpuidle: using governor menu
[    1.553446] TCP cubic registered
[    1.553749] registered taskstats version 1
[    1.553902]   Magic number: 9:940:480
[    1.554047] rtc_cmos 00:03: setting system clock to 2009-05-10 12:27:42 UTC (1241958462)
[    1.554051] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.554054] EDD information not available.
[    1.554111] Freeing unused kernel memory: 536k freed
[    1.554418] Write protecting the kernel read-only data: 4348k
[    1.577913] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.727505] fuse init (API version 7.9)
[    1.852769] processor ACPI0007:00: registered as cooling_device0
[    1.852876] processor ACPI0007:01: registered as cooling_device1
[    2.361807] usbcore: registered new interface driver usbfs
[    2.361845] usbcore: registered new interface driver hub
[    2.372836] usbcore: registered new device driver usb
[    2.378229] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[    2.378233] e100: Copyright(c) 1999-2006 Intel Corporation
[    2.378299] e100 0000:05:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.403363] e100 0000:05:08.0: PME# disabled
[    2.410585] e100: eth0: e100_probe: addr 0xb3002000, irq 20, MAC addr 00:16:76:31:52:fa
[    2.411923] b43-pci-bridge 0000:05:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    2.414099] No dock devices found.
[    2.429269] SCSI subsystem initialized
[    2.447393] libata version 3.00 loaded.
[    2.481757] USB Universal Host Controller Interface driver v3.0
[    2.488690] ssb: Sonics Silicon Backplane found on PCI device 0000:05:01.0
[    2.488803] ata_piix 0000:00:1f.1: version 2.12
[    2.488819] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.488867] ata_piix 0000:00:1f.1: setting latency timer to 64
[    2.489437] scsi0 : ata_piix
[    2.489581] scsi1 : ata_piix
[    2.490628] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x30b0 irq 14
[    2.490632] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x30b8 irq 15
[    2.829086] ata1.00: ATAPI: SONY    DVD RW DRU-710A, BY03, max UDMA/66
[    2.829104] ata1.01: ATAPI: LITE-ON LTR-48126S, 2QS5, max UDMA/33
[    2.844986] ata1.00: configured for UDMA/66
[    2.860842] ata1.01: configured for UDMA/33
[    2.860900] ata2: port disabled. ignoring.
[    2.860955] isa bounce pool size: 16 pages
[    2.861815] scsi 0:0:0:0: CD-ROM            SONY     DVD RW DRU-710A  BY03 PQ: 0 ANSI: 5
[    2.862408] scsi 0:0:1:0: CD-ROM            LITE-ON  LTR-48126S       2QS5 PQ: 0 ANSI: 5
[    2.862563] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.862569] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    2.862618] ata_piix 0000:00:1f.2: setting latency timer to 64
[    2.864143] scsi2 : ata_piix
[    2.864283] scsi3 : ata_piix
[    2.864477] ata3: SATA max UDMA/133 cmd 0x30c8 ctl 0x30e4 bmdma 0x30a0 irq 19
[    2.864482] ata4: SATA max UDMA/133 cmd 0x30c0 ctl 0x30e0 bmdma 0x30a8 irq 19
[    3.036992] ata3.00: ATA-6: ST380817AS, 9.01, max UDMA/133
[    3.036998] ata3.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.037157] ata3.01: ATA-6: WDC WD800JD-23JNC0, 06.01C06, max UDMA/133
[    3.037161] ata3.01: 156312576 sectors, multi 16: LBA 
[    3.052961] ata3.00: configured for UDMA/133
[    3.061029] ata3.01: configured for UDMA/133
[    3.224316] ata4.00: ATA-7: WDC WD800JD-22LSA0, 06.01D06, max UDMA/133
[    3.224322] ata4.00: 156301488 sectors, multi 16: LBA48 
[    3.232323] ata4.00: configured for UDMA/133
[    3.232477] scsi 2:0:0:0: Direct-Access     ATA      ST380817AS       9.01 PQ: 0 ANSI: 5
[    3.232693] scsi 2:0:1:0: Direct-Access     ATA      WDC WD800JD-23JN 06.0 PQ: 0 ANSI: 5
[    3.232857] scsi 3:0:0:0: Direct-Access     ATA      WDC WD800JD-22LS 06.0 PQ: 0 ANSI: 5
[    3.237739] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.237752] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.237757] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.237829] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.237868] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00003080
[    3.238060] usb usb1: configuration #1 chosen from 1 choice
[    3.238099] hub 1-0:1.0: USB hub found
[    3.238110] hub 1-0:1.0: 2 ports detected
[    3.342324] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.342336] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.342341] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.342389] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.342419] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00003060
[    3.342580] usb usb2: configuration #1 chosen from 1 choice
[    3.342619] hub 2-0:1.0: USB hub found
[    3.342629] hub 2-0:1.0: 2 ports detected
[    3.549415] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.549426] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.549430] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.549472] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.549512] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00003040
[    3.549648] usb usb3: configuration #1 chosen from 1 choice
[    3.549684] hub 3-0:1.0: USB hub found
[    3.549695] hub 3-0:1.0: 2 ports detected
[    3.653456] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    3.653465] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    3.653469] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.653516] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.653555] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00003020
[    3.653687] usb usb4: configuration #1 chosen from 1 choice
[    3.653724] hub 4-0:1.0: USB hub found
[    3.653734] hub 4-0:1.0: 2 ports detected
[    3.660519] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    3.756258] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.756276] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.756282] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.756340] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.760233] ehci_hcd 0000:00:1d.7: debug port 1
[    3.760240] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    3.760251] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xb3104000
[    3.788016] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.788968] usb usb5: configuration #1 chosen from 1 choice
[    3.789676] hub 5-0:1.0: USB hub found
[    3.789688] hub 5-0:1.0: 8 ports detected
[    4.012151] scsi 0:0:0:0: Attached scsi generic sg0 type 5
[    4.012203] scsi 0:0:1:0: Attached scsi generic sg1 type 5
[    4.012253] scsi 2:0:0:0: Attached scsi generic sg2 type 0
[    4.012303] scsi 2:0:1:0: Attached scsi generic sg3 type 0
[    4.012350] scsi 3:0:0:0: Attached scsi generic sg4 type 0
[    4.085053] Driver 'sr' needs updating - please use bus_type methods
[    4.090041] Driver 'sd' needs updating - please use bus_type methods
[    4.092703] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    4.092709] Uniform CD-ROM driver Revision: 3.20
[    4.092845] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    4.093947] sr1: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    4.094037] sr 0:0:1:0: Attached scsi CD-ROM sr1
[    4.094181] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    4.094212] sd 2:0:0:0: [sda] Write Protect is off
[    4.094216] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.094269] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.094370] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    4.094399] sd 2:0:0:0: [sda] Write Protect is off
[    4.094403] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.094456] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.094462]  sda: sda1
[    4.101926] sd 2:0:0:0: [sda] Attached SCSI disk
[    4.102068] sd 2:0:1:0: [sdb] 156312576 512-byte hardware sectors (80032 MB)
[    4.102102] sd 2:0:1:0: [sdb] Write Protect is off
[    4.102106] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    4.102164] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.102261] sd 2:0:1:0: [sdb] 156312576 512-byte hardware sectors (80032 MB)
[    4.102292] sd 2:0:1:0: [sdb] Write Protect is off
[    4.102296] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    4.102352] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.102359]  sdb: sdb1 sdb2 < sdb5 >
[    4.122949] sd 2:0:1:0: [sdb] Attached SCSI disk
[    4.123071] sd 3:0:0:0: [sdc] 156301488 512-byte hardware sectors (80026 MB)
[    4.123103] sd 3:0:0:0: [sdc] Write Protect is off
[    4.123107] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    4.123281] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.123374] sd 3:0:0:0: [sdc] 156301488 512-byte hardware sectors (80026 MB)
[    4.123403] sd 3:0:0:0: [sdc] Write Protect is off
[    4.123407] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    4.123460] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.123466]  sdc: sdc1
[    4.133939] sd 3:0:0:0: [sdc] Attached SCSI disk
[    4.188027] usb 2-1: device not accepting address 2, error -71
[    4.244057] hub 2-0:1.0: unable to enumerate USB device on port 1
[    4.616017] usb 2-1: new low speed USB device using uhci_hcd and address 4
[    4.796408] usb 2-1: configuration #1 chosen from 1 choice
[    4.823275] usbcore: registered new interface driver hiddev
[    4.835758] input: Kensington      Kensington USB/PS2 Orbit as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.0/input/input2
[    4.852202] input,hidraw0: USB HID v1.10 Mouse [Kensington      Kensington USB/PS2 Orbit] on usb-0000:00:1d.1-1
[    4.852233] usbcore: registered new interface driver usbhid
[    4.852237] usbhid: v2.6:USB HID core driver
[    7.460708] PM: Starting manual resume from disk
[    7.460714] PM: Resume from partition 8:17
[    7.460717] PM: Checking hibernation image.
[    7.460896] PM: Resume from disk failed.
[    7.517730] kjournald starting.  Commit interval 5 seconds
[    7.517749] EXT3-fs: mounted filesystem with ordered data mode.
[   12.917059] udevd version 124 started
[   13.341865] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   13.400608] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.573509] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   13.592047] ACPI: Power Button (FF) [PWRF]
[   13.592155] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   13.624059] ACPI: Sleep Button (CM) [SLPB]
[   13.661881] iTCO_vendor_support: vendor-support=0
[   13.741875] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   13.741981] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0460)
[   13.742104] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   13.789837] intel_rng: Firmware space is locked read-only. If you can't or
[   13.789840] intel_rng: don't want to disable this in firmware setup, and if
[   13.789842] intel_rng: you are certain that your system has a functional
[   13.789843] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   13.897346] parport_pc 00:08: reported by Plug and Play ACPI
[   13.897409] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   14.321444] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   14.321488] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.495119] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   14.622109] b43-phy0: Broadcom 4318 WLAN found
[   14.672032] logips2pp: Detected unknown logitech mouse model 127
[   14.713708] phy0: Selected rate control algorithm 'pid'
[   14.967992] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
[   15.137964] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input6
[   16.966538] lp0: using parport0 (interrupt-driven).
[   17.179384] Adding 497972k swap on /dev/sdb1.  Priority:-1 extents:1 across:497972k
[   17.751177] EXT3 FS on sdb5, internal journal
[   18.876544] type=1505 audit(1241976480.140:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4287
[   19.065190] type=1505 audit(1241976480.328:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4292
[   19.065400] type=1505 audit(1241976480.328:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4292
[   19.233355] ip_tables: (C) 2000-2006 Netfilter Core Team
[   19.995418] ACPI: WMI: Mapper loaded
[   21.080947] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   21.251557] ppdev: user-space parallel port driver
[   22.678876] Bluetooth: Core ver 2.13
[   22.681587] NET: Registered protocol family 31
[   22.681594] Bluetooth: HCI device and connection manager initialized
[   22.681598] Bluetooth: HCI socket layer initialized
[   22.693849] Bluetooth: L2CAP ver 2.11
[   22.693857] Bluetooth: L2CAP socket layer initialized
[   22.706788] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.706796] Bluetooth: BNEP filters: protocol multicast
[   22.725999] Bridge firewalling registered
[   22.727159] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   22.738444] Bluetooth: SCO (Voice Link) ver 0.6
[   22.738452] Bluetooth: SCO socket layer initialized
[   22.850344] Bluetooth: RFCOMM socket layer initialized
[   22.851611] Bluetooth: RFCOMM TTY layer initialized
[   22.851618] Bluetooth: RFCOMM ver 1.10
[   27.061883] input: b43-phy0 as /devices/virtual/input/input7
[   27.180539] firmware: requesting b43/ucode5.fw
[   27.263711] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   27.263725] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[   27.345517] input: b43-phy0 as /devices/virtual/input/input8
[   27.452038] firmware: requesting b43/ucode5.fw
[   27.455886] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   27.455896] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[   27.704927] NET: Registered protocol family 17
[   41.685565] UDF-fs: No VRS found
[   41.703324] ISO 9660 Extensions: Microsoft Joliet Level 3
[   41.705302] ISOFS: changing to secondary root
[  114.244338] type=1503 audit(1241976575.508:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/5841/net/" pid=5841 profile="/usr/sbin/cupsd"
[  114.315282] NET: Registered protocol family 10
[  114.316524] lo: Disabled Privacy Extensions
[  114.317350] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  114.319763] type=1503 audit(1241976575.580:6): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=5841 profile="/usr/sbin/cupsd"
[  114.319778] type=1503 audit(1241976575.580:7): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=5841 profile="/usr/sbin/cupsd"
[  114.319786] type=1503 audit(1241976575.580:8): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=5841 profile="/usr/sbin/cupsd"
[  114.319794] type=1503 audit(1241976575.580:9): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=5841 profile="/usr/sbin/cupsd"
[  114.319801] type=1503 audit(1241976575.580:10): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=5841 profile="/usr/sbin/cupsd"
[  114.319808] type=1503 audit(1241976575.580:11): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=5841 profile="/usr/sbin/cupsd"
[  114.319815] type=1503 audit(1241976575.580:12): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=5841 profile="/usr/sbin/cupsd"
[  114.319823] type=1503 audit(1241976575.580:13): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=5841 profile="/usr/sbin/cupsd"
[  114.319901] type=1503 audit(1241976575.580:14): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/proc/5841/net/dev" pid=5841 profile="/usr/sbin/cupsd"
[  114.560299] ppdev0: registered pardevice
[  114.608339] ppdev0: unregistered pardevice
[  114.668252] ppdev0: registered pardevice
[  114.716046] ppdev0: unregistered pardevice
[  116.208588] ppdev0: registered pardevice
[  116.256206] ppdev0: unregistered pardevice
kyle@kyle-desktop:~$ clear

kyle@kyle-desktop:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-generic (buildd@yellow) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu10) ) #1 SMP Fri Oct 24 06:40:41 UTC 2008 (Ubuntu 2.6.27-7.14-generic)
[    0.000000] Command line: root=UUID=21222dbe-0b84-4408-b939-a3fea2063593 ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000009f023000 (usable)
[    0.000000]  BIOS-e820: 000000009f023000 - 000000009f071000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000009f071000 - 000000009fea9000 (usable)
[    0.000000]  BIOS-e820: 000000009fea9000 - 000000009fee9000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000009fee9000 - 000000009feed000 (usable)
[    0.000000]  BIOS-e820: 000000009feed000 - 000000009feff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000009feff000 - 000000009ff00000 (usable)
[    0.000000] last_pfn = 0x9ff00 max_arch_pfn = 0x3ffffffff
[    0.000000] init_memory_mapping
[    0.000000]  0000000000 - 009fe00000 page 2M
[    0.000000]  009fe00000 - 009ff00000 page 4k
[    0.000000] kernel direct mapping tables up to 9ff00000 @ 8000-d000
[    0.000000] last_map_addr: 9ff00000 end: 9ff00000
[    0.000000] RAMDISK: 377b5000 - 37fefd74
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP 000FE020, 0014 (r0 INTEL )
[    0.000000] ACPI: RSDT 9FEFDE48, 0038 (r1 INTEL  D945GTP       9B7 MSFT  1000013)
[    0.000000] ACPI: FACP 9FEFCF10, 0074 (r1 INTEL  D945GTP       9B7 MSFT  1000013)
[    0.000000] ACPI: DSDT 9FEF8010, 3FBC (r1 INTEL  D945GTP       9B7 MSFT  1000013)
[    0.000000] ACPI: FACS 9FEE5C40, 0040
[    0.000000] ACPI: APIC 9FEFCE10, 0078 (r1 INTEL  D945GTP       9B7 MSFT  1000013)
[    0.000000] ACPI: WDDT 9FEF7F90, 0040 (r1 INTEL  D945GTP       9B7 MSFT  1000013)
[    0.000000] ACPI: MCFG 9FEF7F10, 003C (r1 INTEL  D945GTP       9B7 MSFT  1000013)
[    0.000000] ACPI: ASF! 9FEFCD10, 00A6 (r32 INTEL  D945GTP       9B7 MSFT  1000013)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000009ff00000
[    0.000000] Bootmem setup node 0 0000000000000000-000000009ff00000
[    0.000000]   NODE_DATA [0000000000001000 - 0000000000005fff]
[    0.000000]   bootmap [000000000000b000 -  000000000001efdf] pages 14
[    0.000000] (6 early reservations) ==> bootmem [0000000000 - 009ff00000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 00008b8f9c]    TEXT DATA BSS ==> [0000200000 - 00008b8f9c]
[    0.000000]   #3 [00377b5000 - 0037fefd74]          RAMDISK ==> [00377b5000 - 0037fefd74]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [0000008000 - 000000b000]          PGTABLE ==> [0000008000 - 000000b000]
[    0.000000] found SMP MP-table at [ffff8800000fe680] 000fe680
[    0.000000]  [ffffe20000000000-ffffe200027fffff] PMD -> [ffff880001200000-ffff8800039fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[5] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0009f023
[    0.000000]     0: 0x0009f071 -> 0x0009fea9
[    0.000000]     0: 0x0009fee9 -> 0x0009feed
[    0.000000]     0: 0x0009feff -> 0x0009ff00
[    0.000000] On node 0 totalpages: 654847
[    0.000000]   DMA zone: 2111 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 640676 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 000000009f023000 - 000000009f071000
[    0.000000] PM: Registered nosave memory: 000000009fea9000 - 000000009fee9000
[    0.000000] PM: Registered nosave memory: 000000009feed000 - 000000009feff000
[    0.000000] Allocating PCI resources starting at a0000000 (gap: 9ff00000:60100000)
[    0.000000] PERCPU: Allocating 64928 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 642787
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=21222dbe-0b84-4408-b939-a3fea2063593 ro quiet splash 
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PMTIMER calibration value
[    0.000000] Detected 2799.935 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Calgary: detecting Calgary via BIOS EBDA area
[    0.004000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.004000] Memory: 2562636k/2620416k available (3112k kernel code, 56752k reserved, 1575k data, 536k init)
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004013] Calibrating delay loop (skipped), value calculated using timer frequency.. 5599.87 BogoMIPS (lpj=11199740)
[    0.004045] Security Framework initialized
[    0.004055] SELinux:  Disabled at boot.
[    0.004076] AppArmor: AppArmor initialized
[    0.004846] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.007682] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.009046] Mount-cache hash table entries: 256
[    0.009315] Initializing cgroup subsys ns
[    0.009321] Initializing cgroup subsys cpuacct
[    0.009324] Initializing cgroup subsys memory
[    0.009348] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.009352] CPU: L2 cache: 1024K
[    0.009356] CPU 0/0 -> Node 0
[    0.009358] CPU: Physical Processor ID: 0
[    0.009360] CPU: Processor Core ID: 0
[    0.009376] CPU0: Thermal monitoring enabled (TM1)
[    0.009380] using mwait in idle threads.
[    0.011861] ACPI: Core revision 20080609
[    0.014090] ACPI: Checking initramfs for custom DSDT
[    0.391011] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.430709] CPU0:               Intel(R) Pentium(R) D CPU 2.80GHz stepping 07
[    0.430715] Using local APIC timer interrupts.
[    0.432029] APIC timer calibration result 12499730
[    0.432032] Detected 12.499 MHz APIC timer.
[    0.432227] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5599.94 BogoMIPS (lpj=11199887)
[    0.004000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.004000] CPU: L2 cache: 1024K
[    0.004000] CPU 1/1 -> Node 0
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] CPU1: Thermal monitoring enabled (TM1)
[    0.520442] CPU1:               Intel(R) Pentium(R) D CPU 2.80GHz stepping 07
[    0.520478] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.524063] Brought up 2 CPUs
[    0.524067] Total of 2 processors activated (11199.81 BogoMIPS).
[    0.524117] CPU0 attaching sched-domain:
[    0.524121]  domain 0: span 0-1 level CPU
[    0.524124]   groups: 0 1
[    0.524129]   domain 1: span 0-1 level NODE
[    0.524132]    groups: 0-1
[    0.524139] CPU1 attaching sched-domain:
[    0.524141]  domain 0: span 0-1 level CPU
[    0.524144]   groups: 1 0
[    0.524148]   domain 1: span 0-1 level NODE
[    0.524151]    groups: 0-1
[    0.524251] net_namespace: 1552 bytes
[    0.524251] Booting paravirtualized kernel on bare hardware
[    0.524357] Time: 12:27:41  Date: 05/10/09
[    0.524406] NET: Registered protocol family 16
[    0.524434] ACPI: bus type pci registered
[    0.524434] PCI: Found Intel Corporation 945G/GZ/P/PL Express Memory Controller Hub without MMCONFIG support.
[    0.524434] PCI: Using configuration type 1 for base access
[    0.528464] ACPI: EC: Look up EC in DSDT
[    0.533202] ACPI: Interpreter enabled
[    0.533206] ACPI: (supports S0 S1 S3 S4 S5)
[    0.533233] ACPI: Using IOAPIC for interrupt routing
[    0.540674] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.540674] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.540674] pci 0000:00:01.0: PME# disabled
[    0.540674] PCI: 0000:00:1b.0 reg 10 64bit mmio: [b3100000, b3103fff]
[    0.540674] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.540674] pci 0000:00:1b.0: PME# disabled
[    0.540674] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.540674] pci 0000:00:1c.0: PME# disabled
[    0.540674] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.540674] pci 0000:00:1c.2: PME# disabled
[    0.540674] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.540674] pci 0000:00:1c.3: PME# disabled
[    0.540674] PCI: 0000:00:1d.0 reg 20 io port: [3080, 309f]
[    0.540674] PCI: 0000:00:1d.1 reg 20 io port: [3060, 307f]
[    0.540674] PCI: 0000:00:1d.2 reg 20 io port: [3040, 305f]
[    0.540674] PCI: 0000:00:1d.3 reg 20 io port: [3020, 303f]
[    0.540683] PCI: 0000:00:1d.7 reg 10 32bit mmio: [b3104000, b31043ff]
[    0.540733] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.540739] pci 0000:00:1d.7: PME# disabled
[    0.540867] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.540874] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[    0.540879] pci 0000:00:1f.0: quirk: region 0500-053f claimed by ICH6 GPIO
[    0.540905] PCI: 0000:00:1f.1 reg 10 io port: [0, 7]
[    0.540912] PCI: 0000:00:1f.1 reg 14 io port: [0, 3]
[    0.540920] PCI: 0000:00:1f.1 reg 18 io port: [0, 7]
[    0.540927] PCI: 0000:00:1f.1 reg 1c io port: [0, 3]
[    0.540934] PCI: 0000:00:1f.1 reg 20 io port: [30b0, 30bf]
[    0.540978] PCI: 0000:00:1f.2 reg 10 io port: [30c8, 30cf]
[    0.540985] PCI: 0000:00:1f.2 reg 14 io port: [30e4, 30e7]
[    0.540992] PCI: 0000:00:1f.2 reg 18 io port: [30c0, 30c7]
[    0.540999] PCI: 0000:00:1f.2 reg 1c io port: [30e0, 30e3]
[    0.541005] PCI: 0000:00:1f.2 reg 20 io port: [30a0, 30af]
[    0.541029] pci 0000:00:1f.2: PME# supported from D3hot
[    0.541034] pci 0000:00:1f.2: PME# disabled
[    0.541079] PCI: 0000:00:1f.3 reg 20 io port: [3000, 301f]
[    0.541145] PCI: 0000:01:00.0 reg 10 32bit mmio: [b2000000, b2ffffff]
[    0.541152] PCI: 0000:01:00.0 reg 14 32bit mmio: [a0000000, afffffff]
[    0.541167] PCI: 0000:01:00.0 reg 1c 64bit mmio: [b0000000, b1ffffff]
[    0.541174] PCI: 0000:01:00.0 reg 24 io port: [2000, 207f]
[    0.541181] PCI: 0000:01:00.0 reg 30 32bit mmio: [fffe0000, ffffffff]
[    0.541234] PCI: bridge 0000:00:01.0 io port: [2000, 2fff]
[    0.541238] PCI: bridge 0000:00:01.0 32bit mmio: [b0000000, b2ffffff]
[    0.541244] PCI: bridge 0000:00:01.0 64bit mmio pref: [a0000000, afffffff]
[    0.541292] PCI: bridge 0000:00:1c.0 32bit mmio: [b3200000, b32fffff]
[    0.541344] PCI: bridge 0000:00:1c.2 32bit mmio: [b3300000, b33fffff]
[    0.541395] PCI: bridge 0000:00:1c.3 32bit mmio: [b3400000, b34fffff]
[    0.541426] PCI: 0000:05:00.0 reg 10 32bit mmio: [b3003000, b30031ff]
[    0.541460] PCI: 0000:05:00.0 reg 30 32bit mmio: [ffff0000, ffffffff]
[    0.541487] PCI: 0000:05:01.0 reg 10 32bit mmio: [b3000000, b3001fff]
[    0.541563] PCI: 0000:05:08.0 reg 10 32bit mmio: [b3002000, b3002fff]
[    0.541571] PCI: 0000:05:08.0 reg 14 io port: [1000, 103f]
[    0.541613] pci 0000:05:08.0: supports D1
[    0.541615] pci 0000:05:08.0: supports D2
[    0.541618] pci 0000:05:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.541625] pci 0000:05:08.0: PME# disabled
[    0.541660] pci 0000:00:1e.0: transparent bridge
[    0.541664] PCI: bridge 0000:00:1e.0 io port: [1000, 1fff]
[    0.541669] PCI: bridge 0000:00:1e.0 32bit mmio: [b3000000, b30fffff]
[    0.541705] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.542269] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[    0.542875] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.543078] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[    0.544189] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[    0.548262] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.548396] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.548581] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    0.548764] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.548946] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11 12)
[    0.549136] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11 12)
[    0.549320] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 *9 10 11 12)
[    0.549502] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 *10 11 12)
[    0.549604] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.549604] pnp: PnP ACPI init
[    0.549604] ACPI: bus type pnp registered
[    0.556368] pnp: PnP ACPI: found 13 devices
[    0.556368] ACPI: ACPI bus type pnp unregistered
[    0.556368] PCI: Using ACPI for IRQ routing
[    0.588048] NET: Registered protocol family 8
[    0.588051] NET: Registered protocol family 20
[    0.588074] NetLabel: Initializing
[    0.588074] NetLabel:  domain hash size = 128
[    0.588074] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.588091] NetLabel:  unlabeled traffic allowed by default
[    0.588117] PCI-GART: No AMD northbridge found.
[    0.588206] hpet clockevent registered
[    0.588211] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.588218] hpet0: 3 64-bit timers, 14318180 Hz
[    0.593535] tracer: 1286 pages allocated for 65536 entries of 80 bytes
[    0.593539]    actual entries 65586
[    0.593672] AppArmor: AppArmor Filesystem Enabled
[    0.593696] ACPI: RTC can wake from S4
[    0.608061] system 00:01: iomem range 0xf0000000-0xf3ffffff has been reserved
[    0.608066] system 00:01: iomem range 0xfed13000-0xfed13fff has been reserved
[    0.608069] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.608073] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.608076] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.608080] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.608083] system 00:01: iomem range 0xfed20000-0xfed9ffff has been reserved
[    0.608086] system 00:01: iomem range 0xc0000-0xdffff has been reserved
[    0.608090] system 00:01: iomem range 0xe0000-0xfffff could not be reserved
[    0.608105] system 00:06: ioport range 0x500-0x53f has been reserved
[    0.608115] system 00:06: ioport range 0x400-0x47f has been reserved
[    0.608118] system 00:06: ioport range 0x680-0x6ff has been reserved
[    0.613642] pci 0000:01:00.0: BAR 6: can't allocate mem resource [0xb0000000-0xafffffff]
[    0.613648] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.613652] pci 0000:00:01.0:   IO window: 0x2000-0x2fff
[    0.613658] pci 0000:00:01.0:   MEM window: 0xb0000000-0xb2ffffff
[    0.613662] pci 0000:00:01.0:   PREFETCH window: 0x000000a0000000-0x000000afffffff
[    0.613668] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.613670] pci 0000:00:1c.0:   IO window: disabled
[    0.613676] pci 0000:00:1c.0:   MEM window: 0xb3200000-0xb32fffff
[    0.613681] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.613688] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:03
[    0.613690] pci 0000:00:1c.2:   IO window: disabled
[    0.613695] pci 0000:00:1c.2:   MEM window: 0xb3300000-0xb33fffff
[    0.613700] pci 0000:00:1c.2:   PREFETCH window: disabled
[    0.613707] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:04
[    0.613709] pci 0000:00:1c.3:   IO window: disabled
[    0.613714] pci 0000:00:1c.3:   MEM window: 0xb3400000-0xb34fffff
[    0.613719] pci 0000:00:1c.3:   PREFETCH window: disabled
[    0.613726] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.613730] pci 0000:00:1e.0:   IO window: 0x1000-0x1fff
[    0.613736] pci 0000:00:1e.0:   MEM window: 0xb3000000-0xb30fffff
[    0.613740] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.613761] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.613766] pci 0000:00:01.0: setting latency timer to 64
[    0.613777] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.613782] pci 0000:00:1c.0: setting latency timer to 64
[    0.613792] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.613797] pci 0000:00:1c.2: setting latency timer to 64
[    0.613807] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.613812] pci 0000:00:1c.3: setting latency timer to 64
[    0.613820] pci 0000:00:1e.0: setting latency timer to 64
[    0.613825] bus: 00 index 0 io port: [0, ffff]
[    0.613827] bus: 00 index 1 mmio: [0, ffffffffffffffff]
[    0.613830] bus: 01 index 0 io port: [2000, 2fff]
[    0.613833] bus: 01 index 1 mmio: [b0000000, b2ffffff]
[    0.613835] bus: 01 index 2 mmio: [a0000000, afffffff]
[    0.613838] bus: 01 index 3 mmio: [0, 0]
[    0.613840] bus: 02 index 0 mmio: [0, 0]
[    0.613842] bus: 02 index 1 mmio: [b3200000, b32fffff]
[    0.613844] bus: 02 index 2 mmio: [0, 0]
[    0.613846] bus: 02 index 3 mmio: [0, 0]
[    0.613849] bus: 03 index 0 mmio: [0, 0]
[    0.613851] bus: 03 index 1 mmio: [b3300000, b33fffff]
[    0.613853] bus: 03 index 2 mmio: [0, 0]
[    0.613855] bus: 03 index 3 mmio: [0, 0]
[    0.613858] bus: 04 index 0 mmio: [0, 0]
[    0.613860] bus: 04 index 1 mmio: [b3400000, b34fffff]
[    0.613862] bus: 04 index 2 mmio: [0, 0]
[    0.613864] bus: 04 index 3 mmio: [0, 0]
[    0.613867] bus: 05 index 0 io port: [1000, 1fff]
[    0.613869] bus: 05 index 1 mmio: [b3000000, b30fffff]
[    0.613871] bus: 05 index 2 mmio: [0, 0]
[    0.613873] bus: 05 index 3 io port: [0, ffff]
[    0.613876] bus: 05 index 4 mmio: [0, ffffffffffffffff]
[    0.613893] NET: Registered protocol family 2
[    0.652286] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.654428] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.659873] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.660524] TCP: Hash tables configured (established 524288 bind 65536)
[    0.660530] TCP reno registered
[    0.672178] NET: Registered protocol family 1
[    0.672340] checking if image is initramfs... it is
[    1.088517] Switched to high resolution mode on CPU 1
[    1.092033] Switched to high resolution mode on CPU 0
[    1.451263] Freeing initrd memory: 8427k freed
[    1.458562] audit: initializing netlink socket (disabled)
[    1.458593] type=2000 audit(1241958461.456:1): initialized
[    1.464653] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.468387] VFS: Disk quotas dquot_6.5.1
[    1.468575] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.468732] msgmni has been set to 5021
[    1.468902] io scheduler noop registered
[    1.468905] io scheduler anticipatory registered
[    1.468908] io scheduler deadline registered
[    1.469082] io scheduler cfq registered (default)
[    1.469312] pci 0000:01:00.0: Boot video device
[    1.469329] pci 0000:05:08.0: Firmware left e100 interrupts enabled; disabling
[    1.469483] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.469523] pcieport-driver 0000:00:01.0: found MSI capability
[    1.469559] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.469683] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.469718] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.469757] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.469820] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.469939] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.469974] pcieport-driver 0000:00:1c.2: found MSI capability
[    1.470012] pci_express 0000:00:1c.2:pcie00: allocate port service
[    1.470081] pci_express 0000:00:1c.2:pcie02: allocate port service
[    1.470204] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.470240] pcieport-driver 0000:00:1c.3: found MSI capability
[    1.470277] pci_express 0000:00:1c.3:pcie00: allocate port service
[    1.470341] pci_express 0000:00:1c.3:pcie02: allocate port service
[    1.520471] Linux agpgart interface v0.103
[    1.520478] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.520662] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.521614] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.524245] brd: module loaded
[    1.524345] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.524591] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.527550] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.527559] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.552679] mice: PS/2 mouse device common for all mice
[    1.552867] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.552896] rtc0: alarms up to one month, hpet irqs
[    1.552962] cpuidle: using governor ladder
[    1.552966] cpuidle: using governor menu
[    1.553446] TCP cubic registered
[    1.553749] registered taskstats version 1
[    1.553902]   Magic number: 9:940:480
[    1.554047] rtc_cmos 00:03: setting system clock to 2009-05-10 12:27:42 UTC (1241958462)
[    1.554051] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.554054] EDD information not available.
[    1.554111] Freeing unused kernel memory: 536k freed
[    1.554418] Write protecting the kernel read-only data: 4348k
[    1.577913] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.727505] fuse init (API version 7.9)
[    1.852769] processor ACPI0007:00: registered as cooling_device0
[    1.852876] processor ACPI0007:01: registered as cooling_device1
[    2.361807] usbcore: registered new interface driver usbfs
[    2.361845] usbcore: registered new interface driver hub
[    2.372836] usbcore: registered new device driver usb
[    2.378229] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[    2.378233] e100: Copyright(c) 1999-2006 Intel Corporation
[    2.378299] e100 0000:05:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.403363] e100 0000:05:08.0: PME# disabled
[    2.410585] e100: eth0: e100_probe: addr 0xb3002000, irq 20, MAC addr 00:16:76:31:52:fa
[    2.411923] b43-pci-bridge 0000:05:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    2.414099] No dock devices found.
[    2.429269] SCSI subsystem initialized
[    2.447393] libata version 3.00 loaded.
[    2.481757] USB Universal Host Controller Interface driver v3.0
[    2.488690] ssb: Sonics Silicon Backplane found on PCI device 0000:05:01.0
[    2.488803] ata_piix 0000:00:1f.1: version 2.12
[    2.488819] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.488867] ata_piix 0000:00:1f.1: setting latency timer to 64
[    2.489437] scsi0 : ata_piix
[    2.489581] scsi1 : ata_piix
[    2.490628] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x30b0 irq 14
[    2.490632] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x30b8 irq 15
[    2.829086] ata1.00: ATAPI: SONY    DVD RW DRU-710A, BY03, max UDMA/66
[    2.829104] ata1.01: ATAPI: LITE-ON LTR-48126S, 2QS5, max UDMA/33
[    2.844986] ata1.00: configured for UDMA/66
[    2.860842] ata1.01: configured for UDMA/33
[    2.860900] ata2: port disabled. ignoring.
[    2.860955] isa bounce pool size: 16 pages
[    2.861815] scsi 0:0:0:0: CD-ROM            SONY     DVD RW DRU-710A  BY03 PQ: 0 ANSI: 5
[    2.862408] scsi 0:0:1:0: CD-ROM            LITE-ON  LTR-48126S       2QS5 PQ: 0 ANSI: 5
[    2.862563] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.862569] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    2.862618] ata_piix 0000:00:1f.2: setting latency timer to 64
[    2.864143] scsi2 : ata_piix
[    2.864283] scsi3 : ata_piix
[    2.864477] ata3: SATA max UDMA/133 cmd 0x30c8 ctl 0x30e4 bmdma 0x30a0 irq 19
[    2.864482] ata4: SATA max UDMA/133 cmd 0x30c0 ctl 0x30e0 bmdma 0x30a8 irq 19
[    3.036992] ata3.00: ATA-6: ST380817AS, 9.01, max UDMA/133
[    3.036998] ata3.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.037157] ata3.01: ATA-6: WDC WD800JD-23JNC0, 06.01C06, max UDMA/133
[    3.037161] ata3.01: 156312576 sectors, multi 16: LBA 
[    3.052961] ata3.00: configured for UDMA/133
[    3.061029] ata3.01: configured for UDMA/133
[    3.224316] ata4.00: ATA-7: WDC WD800JD-22LSA0, 06.01D06, max UDMA/133
[    3.224322] ata4.00: 156301488 sectors, multi 16: LBA48 
[    3.232323] ata4.00: configured for UDMA/133
[    3.232477] scsi 2:0:0:0: Direct-Access     ATA      ST380817AS       9.01 PQ: 0 ANSI: 5
[    3.232693] scsi 2:0:1:0: Direct-Access     ATA      WDC WD800JD-23JN 06.0 PQ: 0 ANSI: 5
[    3.232857] scsi 3:0:0:0: Direct-Access     ATA      WDC WD800JD-22LS 06.0 PQ: 0 ANSI: 5
[    3.237739] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.237752] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.237757] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.237829] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.237868] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00003080
[    3.238060] usb usb1: configuration #1 chosen from 1 choice
[    3.238099] hub 1-0:1.0: USB hub found
[    3.238110] hub 1-0:1.0: 2 ports detected
[    3.342324] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.342336] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.342341] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.342389] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.342419] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00003060
[    3.342580] usb usb2: configuration #1 chosen from 1 choice
[    3.342619] hub 2-0:1.0: USB hub found
[    3.342629] hub 2-0:1.0: 2 ports detected
[    3.549415] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.549426] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.549430] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.549472] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.549512] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00003040
[    3.549648] usb usb3: configuration #1 chosen from 1 choice
[    3.549684] hub 3-0:1.0: USB hub found
[    3.549695] hub 3-0:1.0: 2 ports detected
[    3.653456] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    3.653465] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    3.653469] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.653516] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.653555] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00003020
[    3.653687] usb usb4: configuration #1 chosen from 1 choice
[    3.653724] hub 4-0:1.0: USB hub found
[    3.653734] hub 4-0:1.0: 2 ports detected
[    3.660519] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    3.756258] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.756276] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.756282] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.756340] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.760233] ehci_hcd 0000:00:1d.7: debug port 1
[    3.760240] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    3.760251] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xb3104000
[    3.788016] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.788968] usb usb5: configuration #1 chosen from 1 choice
[    3.789676] hub 5-0:1.0: USB hub found
[    3.789688] hub 5-0:1.0: 8 ports detected
[    4.012151] scsi 0:0:0:0: Attached scsi generic sg0 type 5
[    4.012203] scsi 0:0:1:0: Attached scsi generic sg1 type 5
[    4.012253] scsi 2:0:0:0: Attached scsi generic sg2 type 0
[    4.012303] scsi 2:0:1:0: Attached scsi generic sg3 type 0
[    4.012350] scsi 3:0:0:0: Attached scsi generic sg4 type 0
[    4.085053] Driver 'sr' needs updating - please use bus_type methods
[    4.090041] Driver 'sd' needs updating - please use bus_type methods
[    4.092703] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    4.092709] Uniform CD-ROM driver Revision: 3.20
[    4.092845] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    4.093947] sr1: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    4.094037] sr 0:0:1:0: Attached scsi CD-ROM sr1
[    4.094181] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    4.094212] sd 2:0:0:0: [sda] Write Protect is off
[    4.094216] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.094269] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.094370] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    4.094399] sd 2:0:0:0: [sda] Write Protect is off
[    4.094403] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.094456] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.094462]  sda: sda1
[    4.101926] sd 2:0:0:0: [sda] Attached SCSI disk
[    4.102068] sd 2:0:1:0: [sdb] 156312576 512-byte hardware sectors (80032 MB)
[    4.102102] sd 2:0:1:0: [sdb] Write Protect is off
[    4.102106] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    4.102164] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.102261] sd 2:0:1:0: [sdb] 156312576 512-byte hardware sectors (80032 MB)
[    4.102292] sd 2:0:1:0: [sdb] Write Protect is off
[    4.102296] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    4.102352] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.102359]  sdb: sdb1 sdb2 < sdb5 >
[    4.122949] sd 2:0:1:0: [sdb] Attached SCSI disk
[    4.123071] sd 3:0:0:0: [sdc] 156301488 512-byte hardware sectors (80026 MB)
[    4.123103] sd 3:0:0:0: [sdc] Write Protect is off
[    4.123107] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    4.123281] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.123374] sd 3:0:0:0: [sdc] 156301488 512-byte hardware sectors (80026 MB)
[    4.123403] sd 3:0:0:0: [sdc] Write Protect is off
[    4.123407] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    4.123460] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.123466]  sdc: sdc1
[    4.133939] sd 3:0:0:0: [sdc] Attached SCSI disk
[    4.188027] usb 2-1: device not accepting address 2, error -71
[    4.244057] hub 2-0:1.0: unable to enumerate USB device on port 1
[    4.616017] usb 2-1: new low speed USB device using uhci_hcd and address 4
[    4.796408] usb 2-1: configuration #1 chosen from 1 choice
[    4.823275] usbcore: registered new interface driver hiddev
[    4.835758] input: Kensington      Kensington USB/PS2 Orbit as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.0/input/input2
[    4.852202] input,hidraw0: USB HID v1.10 Mouse [Kensington      Kensington USB/PS2 Orbit] on usb-0000:00:1d.1-1
[    4.852233] usbcore: registered new interface driver usbhid
[    4.852237] usbhid: v2.6:USB HID core driver
[    7.460708] PM: Starting manual resume from disk
[    7.460714] PM: Resume from partition 8:17
[    7.460717] PM: Checking hibernation image.
[    7.460896] PM: Resume from disk failed.
[    7.517730] kjournald starting.  Commit interval 5 seconds
[    7.517749] EXT3-fs: mounted filesystem with ordered data mode.
[   12.917059] udevd version 124 started
[   13.341865] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   13.400608] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.573509] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   13.592047] ACPI: Power Button (FF) [PWRF]
[   13.592155] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   13.624059] ACPI: Sleep Button (CM) [SLPB]
[   13.661881] iTCO_vendor_support: vendor-support=0
[   13.741875] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   13.741981] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0460)
[   13.742104] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   13.789837] intel_rng: Firmware space is locked read-only. If you can't or
[   13.789840] intel_rng: don't want to disable this in firmware setup, and if
[   13.789842] intel_rng: you are certain that your system has a functional
[   13.789843] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   13.897346] parport_pc 00:08: reported by Plug and Play ACPI
[   13.897409] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   14.321444] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   14.321488] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.495119] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   14.622109] b43-phy0: Broadcom 4318 WLAN found
[   14.672032] logips2pp: Detected unknown logitech mouse model 127
[   14.713708] phy0: Selected rate control algorithm 'pid'
[   14.967992] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
[   15.137964] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input6
[   16.966538] lp0: using parport0 (interrupt-driven).
[   17.179384] Adding 497972k swap on /dev/sdb1.  Priority:-1 extents:1 across:497972k
[   17.751177] EXT3 FS on sdb5, internal journal
[   18.876544] type=1505 audit(1241976480.140:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4287
[   19.065190] type=1505 audit(1241976480.328:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4292
[   19.065400] type=1505 audit(1241976480.328:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4292
[   19.233355] ip_tables: (C) 2000-2006 Netfilter Core Team
[   19.995418] ACPI: WMI: Mapper loaded
[   21.080947] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   21.251557] ppdev: user-space parallel port driver
[   22.678876] Bluetooth: Core ver 2.13
[   22.681587] NET: Registered protocol family 31
[   22.681594] Bluetooth: HCI device and connection manager initialized
[   22.681598] Bluetooth: HCI socket layer initialized
[   22.693849] Bluetooth: L2CAP ver 2.11
[   22.693857] Bluetooth: L2CAP socket layer initialized
[   22.706788] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.706796] Bluetooth: BNEP filters: protocol multicast
[   22.725999] Bridge firewalling registered
[   22.727159] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   22.738444] Bluetooth: SCO (Voice Link) ver 0.6
[   22.738452] Bluetooth: SCO socket layer initialized
[   22.850344] Bluetooth: RFCOMM socket layer initialized
[   22.851611] Bluetooth: RFCOMM TTY layer initialized
[   22.851618] Bluetooth: RFCOMM ver 1.10
[   27.061883] input: b43-phy0 as /devices/virtual/input/input7
[   27.180539] firmware: requesting b43/ucode5.fw
[   27.263711] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   27.263725] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[   27.345517] input: b43-phy0 as /devices/virtual/input/input8
[   27.452038] firmware: requesting b43/ucode5.fw
[   27.455886] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   27.455896] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[   27.704927] NET: Registered protocol family 17
[   41.685565] UDF-fs: No VRS found
[   41.703324] ISO 9660 Extensions: Microsoft Joliet Level 3
[   41.705302] ISOFS: changing to secondary root
[  114.244338] type=1503 audit(1241976575.508:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/5841/net/" pid=5841 profile="/usr/sbin/cupsd"
[  114.315282] NET: Registered protocol family 10
[  114.316524] lo: Disabled Privacy Extensions
[  114.317350] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  114.319763] type=1503 audit(1241976575.580:6): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=5841 profile="/usr/sbin/cupsd"
[  114.319778] type=1503 audit(1241976575.580:7): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=5841 profile="/usr/sbin/cupsd"
[  114.319786] type=1503 audit(1241976575.580:8): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=5841 profile="/usr/sbin/cupsd"
[  114.319794] type=1503 audit(1241976575.580:9): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=5841 profile="/usr/sbin/cupsd"
[  114.319801] type=1503 audit(1241976575.580:10): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=5841 profile="/usr/sbin/cupsd"
[  114.319808] type=1503 audit(1241976575.580:11): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=5841 profile="/usr/sbin/cupsd"
[  114.319815] type=1503 audit(1241976575.580:12): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=5841 profile="/usr/sbin/cupsd"
[  114.319823] type=1503 audit(1241976575.580:13): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=5841 profile="/usr/sbin/cupsd"
[  114.319901] type=1503 audit(1241976575.580:14): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/proc/5841/net/dev" pid=5841 profile="/usr/sbin/cupsd"
[  114.560299] ppdev0: registered pardevice
[  114.608339] ppdev0: unregistered pardevice
[  114.668252] ppdev0: registered pardevice
[  114.716046] ppdev0: unregistered pardevice
[  116.208588] ppdev0: registered pardevice
[  116.256206] ppdev0: unregistered pardevice
kyle@kyle-desktop:~$ dmesg | more
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-generic (buildd@yellow) (gcc version 4.3.2 (Ubuntu
 4.3.2-1ubuntu10) ) #1 SMP Fri Oct 24 06:40:41 UTC 2008 (Ubuntu 2.6.27-7.14-generic)
[    0.000000] Command line: root=UUID=21222dbe-0b84-4408-b939-a3fea2063593 ro quiet spl
ash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000009f023000 (usable)
[    0.000000]  BIOS-e820: 000000009f023000 - 000000009f071000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000009f071000 - 000000009fea9000 (usable)
[    0.000000]  BIOS-e820: 000000009fea9000 - 000000009fee9000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000009fee9000 - 000000009feed000 (usable)
[    0.000000]  BIOS-e820: 000000009feed000 - 000000009feff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000009feff000 - 000000009ff00000 (usable)
[    0.000000] last_pfn = 0x9ff00 max_arch_pfn = 0x3ffffffff
[    0.000000] init_memory_mapping
[    0.000000]  0000000000 - 009fe00000 page 2M
[    0.000000]  009fe00000 - 009ff00000 page 4k
[    0.000000] kernel direct mapping tables up to 9ff00000 @ 8000-d000
[    0.000000] last_map_addr: 9ff00000 end: 9ff00000
[    0.000000] RAMDISK: 377b5000 - 37fefd74
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP 000FE020, 0014 (r0 INTEL )
[    0.000000] ACPI: RSDT 9FEFDE48, 0038 (r1 INTEL  D945GTP       9B7 MSFT  1000013)
[    0.000000] ACPI: FACP 9FEFCF10, 0074 (r1 INTEL  D945GTP       9B7 MSFT  1000013)
[    0.000000] ACPI: DSDT 9FEF8010, 3FBC (r1 INTEL  D945GTP       9B7 MSFT  1000013)
[    0.000000] ACPI: FACS 9FEE5C40, 0040
[    0.000000] ACPI: APIC 9FEFCE10, 0078 (r1 INTEL  D945GTP       9B7 MSFT  1000013)
[    0.000000] ACPI: WDDT 9FEF7F90, 0040 (r1 INTEL  D945GTP       9B7 MSFT  1000013)
[    0.000000] ACPI: MCFG 9FEF7F10, 003C (r1 INTEL  D945GTP       9B7 MSFT  1000013)
[    0.000000] ACPI: ASF! 9FEFCD10, 00A6 (r32 INTEL  D945GTP       9B7 MSFT  1000013)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000009ff00000
[    0.000000] Bootmem setup node 0 0000000000000000-000000009ff00000
[    0.000000]   NODE_DATA [0000000000001000 - 0000000000005fff]
[    0.000000]   bootmap [000000000000b000 -  000000000001efdf] pages 14
[    0.000000] (6 early reservations) ==> bootmem [0000000000 - 009ff00000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001
000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008
000]
[    0.000000]   #2 [0000200000 - 00008b8f9c]    TEXT DATA BSS ==> [0000200000 - 00008b8
f9c]
[    0.000000]   #3 [00377b5000 - 0037fefd74]          RAMDISK ==> [00377b5000 - 0037fef
d74]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100
000]
[    0.000000]   #5 [0000008000 - 000000b000]          PGTABLE ==> [0000008000 - 000000b
000]
[    0.000000] found SMP MP-table at [ffff8800000fe680] 000fe680
[    0.000000]  [ffffe20000000000-ffffe200027fffff] PMD -> [ffff880001200000-ffff8800039
fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
kyle@kyle-desktop:~$ clear

kyle@kyle-desktop:~$ dmesg | more
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-generic (buildd@yellow) (gcc version 4.3.2 (Ubuntu
 4.3.2-1ubuntu10) ) #1 SMP Fri Oct 24 06:40:41 UTC 2008 (Ubuntu 2.6.27-7.14-generic)
[    0.000000] Command line: root=UUID=21222dbe-0b84-4408-b939-a3fea2063593 ro quiet spl
ash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000009f023000 (usable)
[    0.000000]  BIOS-e820: 000000009f023000 - 000000009f071000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000009f071000 - 000000009fea9000 (usable)
[    0.000000]  BIOS-e820: 000000009fea9000 - 000000009fee9000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000009fee9000 - 000000009feed000 (usable)
[    0.000000]  BIOS-e820: 000000009feed000 - 000000009feff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000009feff000 - 000000009ff00000 (usable)
[    0.000000] last_pfn = 0x9ff00 max_arch_pfn = 0x3ffffffff
[    0.000000] init_memory_mapping
kyle@kyle-desktop:~$ clear

kyle@kyle-desktop:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-generic (buildd@yellow) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu10) ) #1 SMP Fri Oct 24 06:40:41 UTC 2008 (Ubuntu 2.6.27-7.14-generic)
[    0.000000] Command line: root=UUID=21222dbe-0b84-4408-b939-a3fea2063593 ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000009f023000 (usable)
[    0.000000]  BIOS-e820: 000000009f023000 - 000000009f071000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000009f071000 - 000000009fea9000 (usable)
[    0.000000]  BIOS-e820: 000000009fea9000 - 000000009fee9000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000009fee9000 - 000000009feed000 (usable)
[    0.000000]  BIOS-e820: 000000009feed000 - 000000009feff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000009feff000 - 000000009ff00000 (usable)
[    0.000000] last_pfn = 0x9ff00 max_arch_pfn = 0x3ffffffff
[    0.000000] init_memory_mapping
[    0.000000]  0000000000 - 009fe00000 page 2M
[    0.000000]  009fe00000 - 009ff00000 page 4k
[    0.000000] kernel direct mapping tables up to 9ff00000 @ 8000-d000
[    0.000000] last_map_addr: 9ff00000 end: 9ff00000
[    0.000000] RAMDISK: 377b5000 - 37fefd74
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP 000FE020, 0014 (r0 INTEL )
[    0.000000] ACPI: RSDT 9FEFDE48, 0038 (r1 INTEL  D945GTP       9B7 MSFT  1000013)
[    0.000000] ACPI: FACP 9FEFCF10, 0074 (r1 INTEL  D945GTP       9B7 MSFT  1000013)
[    0.000000] ACPI: DSDT 9FEF8010, 3FBC (r1 INTEL  D945GTP       9B7 MSFT  1000013)
[    0.000000] ACPI: FACS 9FEE5C40, 0040
[    0.000000] ACPI: APIC 9FEFCE10, 0078 (r1 INTEL  D945GTP       9B7 MSFT  1000013)
[    0.000000] ACPI: WDDT 9FEF7F90, 0040 (r1 INTEL  D945GTP       9B7 MSFT  1000013)
[    0.000000] ACPI: MCFG 9FEF7F10, 003C (r1 INTEL  D945GTP       9B7 MSFT  1000013)
[    0.000000] ACPI: ASF! 9FEFCD10, 00A6 (r32 INTEL  D945GTP       9B7 MSFT  1000013)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000009ff00000
[    0.000000] Bootmem setup node 0 0000000000000000-000000009ff00000
[    0.000000]   NODE_DATA [0000000000001000 - 0000000000005fff]
[    0.000000]   bootmap [000000000000b000 -  000000000001efdf] pages 14
[    0.000000] (6 early reservations) ==> bootmem [0000000000 - 009ff00000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 00008b8f9c]    TEXT DATA BSS ==> [0000200000 - 00008b8f9c]
[    0.000000]   #3 [00377b5000 - 0037fefd74]          RAMDISK ==> [00377b5000 - 0037fefd74]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [0000008000 - 000000b000]          PGTABLE ==> [0000008000 - 000000b000]
[    0.000000] found SMP MP-table at [ffff8800000fe680] 000fe680
[    0.000000]  [ffffe20000000000-ffffe200027fffff] PMD -> [ffff880001200000-ffff8800039fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[5] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0009f023
[    0.000000]     0: 0x0009f071 -> 0x0009fea9
[    0.000000]     0: 0x0009fee9 -> 0x0009feed
[    0.000000]     0: 0x0009feff -> 0x0009ff00
[    0.000000] On node 0 totalpages: 654847
[    0.000000]   DMA zone: 2111 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 640676 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 000000009f023000 - 000000009f071000
[    0.000000] PM: Registered nosave memory: 000000009fea9000 - 000000009fee9000
[    0.000000] PM: Registered nosave memory: 000000009feed000 - 000000009feff000
[    0.000000] Allocating PCI resources starting at a0000000 (gap: 9ff00000:60100000)
[    0.000000] PERCPU: Allocating 64928 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 642787
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=21222dbe-0b84-4408-b939-a3fea2063593 ro quiet splash 
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PMTIMER calibration value
[    0.000000] Detected 2799.935 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Calgary: detecting Calgary via BIOS EBDA area
[    0.004000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.004000] Memory: 2562636k/2620416k available (3112k kernel code, 56752k reserved, 1575k data, 536k init)
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004013] Calibrating delay loop (skipped), value calculated using timer frequency.. 5599.87 BogoMIPS (lpj=11199740)
[    0.004045] Security Framework initialized
[    0.004055] SELinux:  Disabled at boot.
[    0.004076] AppArmor: AppArmor initialized
[    0.004846] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.007682] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.009046] Mount-cache hash table entries: 256
[    0.009315] Initializing cgroup subsys ns
[    0.009321] Initializing cgroup subsys cpuacct
[    0.009324] Initializing cgroup subsys memory
[    0.009348] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.009352] CPU: L2 cache: 1024K
[    0.009356] CPU 0/0 -> Node 0
[    0.009358] CPU: Physical Processor ID: 0
[    0.009360] CPU: Processor Core ID: 0
[    0.009376] CPU0: Thermal monitoring enabled (TM1)
[    0.009380] using mwait in idle threads.
[    0.011861] ACPI: Core revision 20080609
[    0.014090] ACPI: Checking initramfs for custom DSDT
[    0.391011] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.430709] CPU0:               Intel(R) Pentium(R) D CPU 2.80GHz stepping 07
[    0.430715] Using local APIC timer interrupts.
[    0.432029] APIC timer calibration result 12499730
[    0.432032] Detected 12.499 MHz APIC timer.
[    0.432227] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5599.94 BogoMIPS (lpj=11199887)
[    0.004000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.004000] CPU: L2 cache: 1024K
[    0.004000] CPU 1/1 -> Node 0
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] CPU1: Thermal monitoring enabled (TM1)
[    0.520442] CPU1:               Intel(R) Pentium(R) D CPU 2.80GHz stepping 07
[    0.520478] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.524063] Brought up 2 CPUs
[    0.524067] Total of 2 processors activated (11199.81 BogoMIPS).
[    0.524117] CPU0 attaching sched-domain:
[    0.524121]  domain 0: span 0-1 level CPU
[    0.524124]   groups: 0 1
[    0.524129]   domain 1: span 0-1 level NODE
[    0.524132]    groups: 0-1
[    0.524139] CPU1 attaching sched-domain:
[    0.524141]  domain 0: span 0-1 level CPU
[    0.524144]   groups: 1 0
[    0.524148]   domain 1: span 0-1 level NODE
[    0.524151]    groups: 0-1
[    0.524251] net_namespace: 1552 bytes
[    0.524251] Booting paravirtualized kernel on bare hardware
[    0.524357] Time: 12:27:41  Date: 05/10/09
[    0.524406] NET: Registered protocol family 16
[    0.524434] ACPI: bus type pci registered
[    0.524434] PCI: Found Intel Corporation 945G/GZ/P/PL Express Memory Controller Hub without MMCONFIG support.
[    0.524434] PCI: Using configuration type 1 for base access
[    0.528464] ACPI: EC: Look up EC in DSDT
[    0.533202] ACPI: Interpreter enabled
[    0.533206] ACPI: (supports S0 S1 S3 S4 S5)
[    0.533233] ACPI: Using IOAPIC for interrupt routing
[    0.540674] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.540674] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.540674] pci 0000:00:01.0: PME# disabled
[    0.540674] PCI: 0000:00:1b.0 reg 10 64bit mmio: [b3100000, b3103fff]
[    0.540674] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.540674] pci 0000:00:1b.0: PME# disabled
[    0.540674] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.540674] pci 0000:00:1c.0: PME# disabled
[    0.540674] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.540674] pci 0000:00:1c.2: PME# disabled
[    0.540674] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.540674] pci 0000:00:1c.3: PME# disabled
[    0.540674] PCI: 0000:00:1d.0 reg 20 io port: [3080, 309f]
[    0.540674] PCI: 0000:00:1d.1 reg 20 io port: [3060, 307f]
[    0.540674] PCI: 0000:00:1d.2 reg 20 io port: [3040, 305f]
[    0.540674] PCI: 0000:00:1d.3 reg 20 io port: [3020, 303f]
[    0.540683] PCI: 0000:00:1d.7 reg 10 32bit mmio: [b3104000, b31043ff]
[    0.540733] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.540739] pci 0000:00:1d.7: PME# disabled
[    0.540867] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.540874] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[    0.540879] pci 0000:00:1f.0: quirk: region 0500-053f claimed by ICH6 GPIO
[    0.540905] PCI: 0000:00:1f.1 reg 10 io port: [0, 7]
[    0.540912] PCI: 0000:00:1f.1 reg 14 io port: [0, 3]
[    0.540920] PCI: 0000:00:1f.1 reg 18 io port: [0, 7]
[    0.540927] PCI: 0000:00:1f.1 reg 1c io port: [0, 3]
[    0.540934] PCI: 0000:00:1f.1 reg 20 io port: [30b0, 30bf]
[    0.540978] PCI: 0000:00:1f.2 reg 10 io port: [30c8, 30cf]
[    0.540985] PCI: 0000:00:1f.2 reg 14 io port: [30e4, 30e7]
[    0.540992] PCI: 0000:00:1f.2 reg 18 io port: [30c0, 30c7]
[    0.540999] PCI: 0000:00:1f.2 reg 1c io port: [30e0, 30e3]
[    0.541005] PCI: 0000:00:1f.2 reg 20 io port: [30a0, 30af]
[    0.541029] pci 0000:00:1f.2: PME# supported from D3hot
[    0.541034] pci 0000:00:1f.2: PME# disabled
[    0.541079] PCI: 0000:00:1f.3 reg 20 io port: [3000, 301f]
[    0.541145] PCI: 0000:01:00.0 reg 10 32bit mmio: [b2000000, b2ffffff]
[    0.541152] PCI: 0000:01:00.0 reg 14 32bit mmio: [a0000000, afffffff]
[    0.541167] PCI: 0000:01:00.0 reg 1c 64bit mmio: [b0000000, b1ffffff]
[    0.541174] PCI: 0000:01:00.0 reg 24 io port: [2000, 207f]
[    0.541181] PCI: 0000:01:00.0 reg 30 32bit mmio: [fffe0000, ffffffff]
[    0.541234] PCI: bridge 0000:00:01.0 io port: [2000, 2fff]
[    0.541238] PCI: bridge 0000:00:01.0 32bit mmio: [b0000000, b2ffffff]
[    0.541244] PCI: bridge 0000:00:01.0 64bit mmio pref: [a0000000, afffffff]
[    0.541292] PCI: bridge 0000:00:1c.0 32bit mmio: [b3200000, b32fffff]
[    0.541344] PCI: bridge 0000:00:1c.2 32bit mmio: [b3300000, b33fffff]
[    0.541395] PCI: bridge 0000:00:1c.3 32bit mmio: [b3400000, b34fffff]
[    0.541426] PCI: 0000:05:00.0 reg 10 32bit mmio: [b3003000, b30031ff]
[    0.541460] PCI: 0000:05:00.0 reg 30 32bit mmio: [ffff0000, ffffffff]
[    0.541487] PCI: 0000:05:01.0 reg 10 32bit mmio: [b3000000, b3001fff]
[    0.541563] PCI: 0000:05:08.0 reg 10 32bit mmio: [b3002000, b3002fff]
[    0.541571] PCI: 0000:05:08.0 reg 14 io port: [1000, 103f]
[    0.541613] pci 0000:05:08.0: supports D1
[    0.541615] pci 0000:05:08.0: supports D2
[    0.541618] pci 0000:05:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.541625] pci 0000:05:08.0: PME# disabled
[    0.541660] pci 0000:00:1e.0: transparent bridge
[    0.541664] PCI: bridge 0000:00:1e.0 io port: [1000, 1fff]
[    0.541669] PCI: bridge 0000:00:1e.0 32bit mmio: [b3000000, b30fffff]
[    0.541705] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.542269] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[    0.542875] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.543078] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[    0.544189] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[    0.548262] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.548396] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.548581] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    0.548764] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.548946] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11 12)
[    0.549136] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11 12)
[    0.549320] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 *9 10 11 12)
[    0.549502] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 *10 11 12)
[    0.549604] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.549604] pnp: PnP ACPI init
[    0.549604] ACPI: bus type pnp registered
[    0.556368] pnp: PnP ACPI: found 13 devices
[    0.556368] ACPI: ACPI bus type pnp unregistered
[    0.556368] PCI: Using ACPI for IRQ routing
[    0.588048] NET: Registered protocol family 8
[    0.588051] NET: Registered protocol family 20
[    0.588074] NetLabel: Initializing
[    0.588074] NetLabel:  domain hash size = 128
[    0.588074] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.588091] NetLabel:  unlabeled traffic allowed by default
[    0.588117] PCI-GART: No AMD northbridge found.
[    0.588206] hpet clockevent registered
[    0.588211] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.588218] hpet0: 3 64-bit timers, 14318180 Hz
[    0.593535] tracer: 1286 pages allocated for 65536 entries of 80 bytes
[    0.593539]    actual entries 65586
[    0.593672] AppArmor: AppArmor Filesystem Enabled
[    0.593696] ACPI: RTC can wake from S4
[    0.608061] system 00:01: iomem range 0xf0000000-0xf3ffffff has been reserved
[    0.608066] system 00:01: iomem range 0xfed13000-0xfed13fff has been reserved
[    0.608069] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.608073] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.608076] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.608080] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.608083] system 00:01: iomem range 0xfed20000-0xfed9ffff has been reserved
[    0.608086] system 00:01: iomem range 0xc0000-0xdffff has been reserved
[    0.608090] system 00:01: iomem range 0xe0000-0xfffff could not be reserved
[    0.608105] system 00:06: ioport range 0x500-0x53f has been reserved
[    0.608115] system 00:06: ioport range 0x400-0x47f has been reserved
[    0.608118] system 00:06: ioport range 0x680-0x6ff has been reserved
[    0.613642] pci 0000:01:00.0: BAR 6: can't allocate mem resource [0xb0000000-0xafffffff]
[    0.613648] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.613652] pci 0000:00:01.0:   IO window: 0x2000-0x2fff
[    0.613658] pci 0000:00:01.0:   MEM window: 0xb0000000-0xb2ffffff
[    0.613662] pci 0000:00:01.0:   PREFETCH window: 0x000000a0000000-0x000000afffffff
[    0.613668] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.613670] pci 0000:00:1c.0:   IO window: disabled
[    0.613676] pci 0000:00:1c.0:   MEM window: 0xb3200000-0xb32fffff
[    0.613681] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.613688] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:03
[    0.613690] pci 0000:00:1c.2:   IO window: disabled
[    0.613695] pci 0000:00:1c.2:   MEM window: 0xb3300000-0xb33fffff
[    0.613700] pci 0000:00:1c.2:   PREFETCH window: disabled
[    0.613707] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:04
[    0.613709] pci 0000:00:1c.3:   IO window: disabled
[    0.613714] pci 0000:00:1c.3:   MEM window: 0xb3400000-0xb34fffff
[    0.613719] pci 0000:00:1c.3:   PREFETCH window: disabled
[    0.613726] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.613730] pci 0000:00:1e.0:   IO window: 0x1000-0x1fff
[    0.613736] pci 0000:00:1e.0:   MEM window: 0xb3000000-0xb30fffff
[    0.613740] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.613761] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.613766] pci 0000:00:01.0: setting latency timer to 64
[    0.613777] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.613782] pci 0000:00:1c.0: setting latency timer to 64
[    0.613792] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.613797] pci 0000:00:1c.2: setting latency timer to 64
[    0.613807] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.613812] pci 0000:00:1c.3: setting latency timer to 64
[    0.613820] pci 0000:00:1e.0: setting latency timer to 64
[    0.613825] bus: 00 index 0 io port: [0, ffff]
[    0.613827] bus: 00 index 1 mmio: [0, ffffffffffffffff]
[    0.613830] bus: 01 index 0 io port: [2000, 2fff]
[    0.613833] bus: 01 index 1 mmio: [b0000000, b2ffffff]
[    0.613835] bus: 01 index 2 mmio: [a0000000, afffffff]
[    0.613838] bus: 01 index 3 mmio: [0, 0]
[    0.613840] bus: 02 index 0 mmio: [0, 0]
[    0.613842] bus: 02 index 1 mmio: [b3200000, b32fffff]
[    0.613844] bus: 02 index 2 mmio: [0, 0]
[    0.613846] bus: 02 index 3 mmio: [0, 0]
[    0.613849] bus: 03 index 0 mmio: [0, 0]
[    0.613851] bus: 03 index 1 mmio: [b3300000, b33fffff]
[    0.613853] bus: 03 index 2 mmio: [0, 0]
[    0.613855] bus: 03 index 3 mmio: [0, 0]
[    0.613858] bus: 04 index 0 mmio: [0, 0]
[    0.613860] bus: 04 index 1 mmio: [b3400000, b34fffff]
[    0.613862] bus: 04 index 2 mmio: [0, 0]
[    0.613864] bus: 04 index 3 mmio: [0, 0]
[    0.613867] bus: 05 index 0 io port: [1000, 1fff]
[    0.613869] bus: 05 index 1 mmio: [b3000000, b30fffff]
[    0.613871] bus: 05 index 2 mmio: [0, 0]
[    0.613873] bus: 05 index 3 io port: [0, ffff]
[    0.613876] bus: 05 index 4 mmio: [0, ffffffffffffffff]
[    0.613893] NET: Registered protocol family 2
[    0.652286] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.654428] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.659873] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.660524] TCP: Hash tables configured (established 524288 bind 65536)
[    0.660530] TCP reno registered
[    0.672178] NET: Registered protocol family 1
[    0.672340] checking if image is initramfs... it is
[    1.088517] Switched to high resolution mode on CPU 1
[    1.092033] Switched to high resolution mode on CPU 0
[    1.451263] Freeing initrd memory: 8427k freed
[    1.458562] audit: initializing netlink socket (disabled)
[    1.458593] type=2000 audit(1241958461.456:1): initialized
[    1.464653] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.468387] VFS: Disk quotas dquot_6.5.1
[    1.468575] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.468732] msgmni has been set to 5021
[    1.468902] io scheduler noop registered
[    1.468905] io scheduler anticipatory registered
[    1.468908] io scheduler deadline registered
[    1.469082] io scheduler cfq registered (default)
[    1.469312] pci 0000:01:00.0: Boot video device
[    1.469329] pci 0000:05:08.0: Firmware left e100 interrupts enabled; disabling
[    1.469483] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.469523] pcieport-driver 0000:00:01.0: found MSI capability
[    1.469559] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.469683] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.469718] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.469757] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.469820] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.469939] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.469974] pcieport-driver 0000:00:1c.2: found MSI capability
[    1.470012] pci_express 0000:00:1c.2:pcie00: allocate port service
[    1.470081] pci_express 0000:00:1c.2:pcie02: allocate port service
[    1.470204] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.470240] pcieport-driver 0000:00:1c.3: found MSI capability
[    1.470277] pci_express 0000:00:1c.3:pcie00: allocate port service
[    1.470341] pci_express 0000:00:1c.3:pcie02: allocate port service
[    1.520471] Linux agpgart interface v0.103
[    1.520478] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.520662] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.521614] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.524245] brd: module loaded
[    1.524345] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.524591] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.527550] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.527559] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.552679] mice: PS/2 mouse device common for all mice
[    1.552867] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.552896] rtc0: alarms up to one month, hpet irqs
[    1.552962] cpuidle: using governor ladder
[    1.552966] cpuidle: using governor menu
[    1.553446] TCP cubic registered
[    1.553749] registered taskstats version 1
[    1.553902]   Magic number: 9:940:480
[    1.554047] rtc_cmos 00:03: setting system clock to 2009-05-10 12:27:42 UTC (1241958462)
[    1.554051] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.554054] EDD information not available.
[    1.554111] Freeing unused kernel memory: 536k freed
[    1.554418] Write protecting the kernel read-only data: 4348k
[    1.577913] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.727505] fuse init (API version 7.9)
[    1.852769] processor ACPI0007:00: registered as cooling_device0
[    1.852876] processor ACPI0007:01: registered as cooling_device1
[    2.361807] usbcore: registered new interface driver usbfs
[    2.361845] usbcore: registered new interface driver hub
[    2.372836] usbcore: registered new device driver usb
[    2.378229] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[    2.378233] e100: Copyright(c) 1999-2006 Intel Corporation
[    2.378299] e100 0000:05:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.403363] e100 0000:05:08.0: PME# disabled
[    2.410585] e100: eth0: e100_probe: addr 0xb3002000, irq 20, MAC addr 00:16:76:31:52:fa
[    2.411923] b43-pci-bridge 0000:05:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    2.414099] No dock devices found.
[    2.429269] SCSI subsystem initialized
[    2.447393] libata version 3.00 loaded.
[    2.481757] USB Universal Host Controller Interface driver v3.0
[    2.488690] ssb: Sonics Silicon Backplane found on PCI device 0000:05:01.0
[    2.488803] ata_piix 0000:00:1f.1: version 2.12
[    2.488819] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.488867] ata_piix 0000:00:1f.1: setting latency timer to 64
[    2.489437] scsi0 : ata_piix
[    2.489581] scsi1 : ata_piix
[    2.490628] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x30b0 irq 14
[    2.490632] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x30b8 irq 15
[    2.829086] ata1.00: ATAPI: SONY    DVD RW DRU-710A, BY03, max UDMA/66
[    2.829104] ata1.01: ATAPI: LITE-ON LTR-48126S, 2QS5, max UDMA/33
[    2.844986] ata1.00: configured for UDMA/66
[    2.860842] ata1.01: configured for UDMA/33
[    2.860900] ata2: port disabled. ignoring.
[    2.860955] isa bounce pool size: 16 pages
[    2.861815] scsi 0:0:0:0: CD-ROM            SONY     DVD RW DRU-710A  BY03 PQ: 0 ANSI: 5
[    2.862408] scsi 0:0:1:0: CD-ROM            LITE-ON  LTR-48126S       2QS5 PQ: 0 ANSI: 5
[    2.862563] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.862569] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    2.862618] ata_piix 0000:00:1f.2: setting latency timer to 64
[    2.864143] scsi2 : ata_piix
[    2.864283] scsi3 : ata_piix
[    2.864477] ata3: SATA max UDMA/133 cmd 0x30c8 ctl 0x30e4 bmdma 0x30a0 irq 19
[    2.864482] ata4: SATA max UDMA/133 cmd 0x30c0 ctl 0x30e0 bmdma 0x30a8 irq 19
[    3.036992] ata3.00: ATA-6: ST380817AS, 9.01, max UDMA/133
[    3.036998] ata3.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.037157] ata3.01: ATA-6: WDC WD800JD-23JNC0, 06.01C06, max UDMA/133
[    3.037161] ata3.01: 156312576 sectors, multi 16: LBA 
[    3.052961] ata3.00: configured for UDMA/133
[    3.061029] ata3.01: configured for UDMA/133
[    3.224316] ata4.00: ATA-7: WDC WD800JD-22LSA0, 06.01D06, max UDMA/133
[    3.224322] ata4.00: 156301488 sectors, multi 16: LBA48 
[    3.232323] ata4.00: configured for UDMA/133
[    3.232477] scsi 2:0:0:0: Direct-Access     ATA      ST380817AS       9.01 PQ: 0 ANSI: 5
[    3.232693] scsi 2:0:1:0: Direct-Access     ATA      WDC WD800JD-23JN 06.0 PQ: 0 ANSI: 5
[    3.232857] scsi 3:0:0:0: Direct-Access     ATA      WDC WD800JD-22LS 06.0 PQ: 0 ANSI: 5
[    3.237739] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.237752] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.237757] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.237829] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.237868] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00003080
[    3.238060] usb usb1: configuration #1 chosen from 1 choice
[    3.238099] hub 1-0:1.0: USB hub found
[    3.238110] hub 1-0:1.0: 2 ports detected
[    3.342324] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.342336] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.342341] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.342389] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.342419] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00003060
[    3.342580] usb usb2: configuration #1 chosen from 1 choice
[    3.342619] hub 2-0:1.0: USB hub found
[    3.342629] hub 2-0:1.0: 2 ports detected
[    3.549415] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.549426] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.549430] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.549472] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.549512] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00003040
[    3.549648] usb usb3: configuration #1 chosen from 1 choice
[    3.549684] hub 3-0:1.0: USB hub found
[    3.549695] hub 3-0:1.0: 2 ports detected
[    3.653456] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    3.653465] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    3.653469] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.653516] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.653555] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00003020
[    3.653687] usb usb4: configuration #1 chosen from 1 choice
[    3.653724] hub 4-0:1.0: USB hub found
[    3.653734] hub 4-0:1.0: 2 ports detected
[    3.660519] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    3.756258] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.756276] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.756282] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.756340] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.760233] ehci_hcd 0000:00:1d.7: debug port 1
[    3.760240] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    3.760251] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xb3104000
[    3.788016] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.788968] usb usb5: configuration #1 chosen from 1 choice
[    3.789676] hub 5-0:1.0: USB hub found
[    3.789688] hub 5-0:1.0: 8 ports detected
[    4.012151] scsi 0:0:0:0: Attached scsi generic sg0 type 5
[    4.012203] scsi 0:0:1:0: Attached scsi generic sg1 type 5
[    4.012253] scsi 2:0:0:0: Attached scsi generic sg2 type 0
[    4.012303] scsi 2:0:1:0: Attached scsi generic sg3 type 0
[    4.012350] scsi 3:0:0:0: Attached scsi generic sg4 type 0
[    4.085053] Driver 'sr' needs updating - please use bus_type methods
[    4.090041] Driver 'sd' needs updating - please use bus_type methods
[    4.092703] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    4.092709] Uniform CD-ROM driver Revision: 3.20
[    4.092845] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    4.093947] sr1: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    4.094037] sr 0:0:1:0: Attached scsi CD-ROM sr1
[    4.094181] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    4.094212] sd 2:0:0:0: [sda] Write Protect is off
[    4.094216] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.094269] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.094370] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    4.094399] sd 2:0:0:0: [sda] Write Protect is off
[    4.094403] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.094456] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.094462]  sda: sda1
[    4.101926] sd 2:0:0:0: [sda] Attached SCSI disk
[    4.102068] sd 2:0:1:0: [sdb] 156312576 512-byte hardware sectors (80032 MB)
[    4.102102] sd 2:0:1:0: [sdb] Write Protect is off
[    4.102106] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    4.102164] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.102261] sd 2:0:1:0: [sdb] 156312576 512-byte hardware sectors (80032 MB)
[    4.102292] sd 2:0:1:0: [sdb] Write Protect is off
[    4.102296] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    4.102352] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.102359]  sdb: sdb1 sdb2 < sdb5 >
[    4.122949] sd 2:0:1:0: [sdb] Attached SCSI disk
[    4.123071] sd 3:0:0:0: [sdc] 156301488 512-byte hardware sectors (80026 MB)
[    4.123103] sd 3:0:0:0: [sdc] Write Protect is off
[    4.123107] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    4.123281] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.123374] sd 3:0:0:0: [sdc] 156301488 512-byte hardware sectors (80026 MB)
[    4.123403] sd 3:0:0:0: [sdc] Write Protect is off
[    4.123407] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    4.123460] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.123466]  sdc: sdc1
[    4.133939] sd 3:0:0:0: [sdc] Attached SCSI disk
[    4.188027] usb 2-1: device not accepting address 2, error -71
[    4.244057] hub 2-0:1.0: unable to enumerate USB device on port 1
[    4.616017] usb 2-1: new low speed USB device using uhci_hcd and address 4
[    4.796408] usb 2-1: configuration #1 chosen from 1 choice
[    4.823275] usbcore: registered new interface driver hiddev
[    4.835758] input: Kensington      Kensington USB/PS2 Orbit as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.0/input/input2
[    4.852202] input,hidraw0: USB HID v1.10 Mouse [Kensington      Kensington USB/PS2 Orbit] on usb-0000:00:1d.1-1
[    4.852233] usbcore: registered new interface driver usbhid
[    4.852237] usbhid: v2.6:USB HID core driver
[    7.460708] PM: Starting manual resume from disk
[    7.460714] PM: Resume from partition 8:17
[    7.460717] PM: Checking hibernation image.
[    7.460896] PM: Resume from disk failed.
[    7.517730] kjournald starting.  Commit interval 5 seconds
[    7.517749] EXT3-fs: mounted filesystem with ordered data mode.
[   12.917059] udevd version 124 started
[   13.341865] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   13.400608] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.573509] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   13.592047] ACPI: Power Button (FF) [PWRF]
[   13.592155] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   13.624059] ACPI: Sleep Button (CM) [SLPB]
[   13.661881] iTCO_vendor_support: vendor-support=0
[   13.741875] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   13.741981] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0460)
[   13.742104] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   13.789837] intel_rng: Firmware space is locked read-only. If you can't or
[   13.789840] intel_rng: don't want to disable this in firmware setup, and if
[   13.789842] intel_rng: you are certain that your system has a functional
[   13.789843] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   13.897346] parport_pc 00:08: reported by Plug and Play ACPI
[   13.897409] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   14.321444] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   14.321488] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.495119] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   14.622109] b43-phy0: Broadcom 4318 WLAN found
[   14.672032] logips2pp: Detected unknown logitech mouse model 127
[   14.713708] phy0: Selected rate control algorithm 'pid'
[   14.967992] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
[   15.137964] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input6
[   16.966538] lp0: using parport0 (interrupt-driven).
[   17.179384] Adding 497972k swap on /dev/sdb1.  Priority:-1 extents:1 across:497972k
[   17.751177] EXT3 FS on sdb5, internal journal
[   18.876544] type=1505 audit(1241976480.140:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4287
[   19.065190] type=1505 audit(1241976480.328:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4292
[   19.065400] type=1505 audit(1241976480.328:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4292
[   19.233355] ip_tables: (C) 2000-2006 Netfilter Core Team
[   19.995418] ACPI: WMI: Mapper loaded
[   21.080947] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   21.251557] ppdev: user-space parallel port driver
[   22.678876] Bluetooth: Core ver 2.13
[   22.681587] NET: Registered protocol family 31
[   22.681594] Bluetooth: HCI device and connection manager initialized
[   22.681598] Bluetooth: HCI socket layer initialized
[   22.693849] Bluetooth: L2CAP ver 2.11
[   22.693857] Bluetooth: L2CAP socket layer initialized
[   22.706788] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.706796] Bluetooth: BNEP filters: protocol multicast
[   22.725999] Bridge firewalling registered
[   22.727159] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   22.738444] Bluetooth: SCO (Voice Link) ver 0.6
[   22.738452] Bluetooth: SCO socket layer initialized
[   22.850344] Bluetooth: RFCOMM socket layer initialized
[   22.851611] Bluetooth: RFCOMM TTY layer initialized
[   22.851618] Bluetooth: RFCOMM ver 1.10
[   27.061883] input: b43-phy0 as /devices/virtual/input/input7
[   27.180539] firmware: requesting b43/ucode5.fw
[   27.263711] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   27.263725] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[   27.345517] input: b43-phy0 as /devices/virtual/input/input8
[   27.452038] firmware: requesting b43/ucode5.fw
[   27.455886] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   27.455896] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[   27.704927] NET: Registered protocol family 17
[   41.685565] UDF-fs: No VRS found
[   41.703324] ISO 9660 Extensions: Microsoft Joliet Level 3
[   41.705302] ISOFS: changing to secondary root
[  114.244338] type=1503 audit(1241976575.508:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/5841/net/" pid=5841 profile="/usr/sbin/cupsd"
[  114.315282] NET: Registered protocol family 10
[  114.316524] lo: Disabled Privacy Extensions
[  114.317350] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  114.319763] type=1503 audit(1241976575.580:6): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=5841 profile="/usr/sbin/cupsd"
[  114.319778] type=1503 audit(1241976575.580:7): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=5841 profile="/usr/sbin/cupsd"
[  114.319786] type=1503 audit(1241976575.580:8): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=5841 profile="/usr/sbin/cupsd"
[  114.319794] type=1503 audit(1241976575.580:9): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=5841 profile="/usr/sbin/cupsd"
[  114.319801] type=1503 audit(1241976575.580:10): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=5841 profile="/usr/sbin/cupsd"
[  114.319808] type=1503 audit(1241976575.580:11): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=5841 profile="/usr/sbin/cupsd"
[  114.319815] type=1503 audit(1241976575.580:12): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=5841 profile="/usr/sbin/cupsd"
[  114.319823] type=1503 audit(1241976575.580:13): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=5841 profile="/usr/sbin/cupsd"
[  114.319901] type=1503 audit(1241976575.580:14): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/proc/5841/net/dev" pid=5841 profile="/usr/sbin/cupsd"
[  114.560299] ppdev0: registered pardevice
[  114.608339] ppdev0: unregistered pardevice
[  114.668252] ppdev0: registered pardevice
[  114.716046] ppdev0: unregistered pardevice
[  116.208588] ppdev0: registered pardevice
[  116.256206] ppdev0: unregistered pardevice
```

---

### Post by Jimshoe02 on 2009-05-11
6 ) Network configuration
Code:

```
kyle@kyle-desktop:~$ sudo lshw -C network
[sudo] password for kyle: 
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:05:01.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:1
       description: Ethernet interface
       product: 82801G (ICH7 Family) LAN Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:05:08.0
       logical name: eth0
       version: 01
       serial: 00:16:76:31:52:fa
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=32 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:22:75:18:7f:26
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 32:d8:c8:74:03:a3
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


```
7 ) Scan for networks:
Code:

```
kyle@kyle-desktop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.
```


8 ) Ubuntu Version:
Code:

```
kyle@kyle-desktop:~$ lsb_release -d
Description:	Ubuntu 8.10
```


9 ) Kernel/architecture (including 32 vs. 64 bit):
Code:

```
kyle@kyle-desktop:~$ uname -mr
2.6.27-7-generic x86_64
```

10 ) Restarting the network:
Code:

```
kyle@kyle-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                           [ OK ]


```



Sorry for my previous lack of any real information.

---

### Post by tospig on 2009-05-11
I'm not sure if this will solve your problem but it worked for me: in one of the how-to's/wiki entrys (the first sticky in the network & wireles forum, section 3) it mentions adding all the other network card drivers to the blacklist, including onboard LAN drivers. 

For me the onboard LAN drivers were conflicting with the wireless card drivers. As soon as I disabled these it worked fine.

---

### Post by Jimshoe02 on 2009-05-11
HOLY CRAP!!!
Thank you so much! That did the trick. I looked through the ndiswrapper howto / tutorial and found that I needed a 64-bit driver. Thanks to you, I am writing this response on my newly connected Ubuntu desktop!

---

