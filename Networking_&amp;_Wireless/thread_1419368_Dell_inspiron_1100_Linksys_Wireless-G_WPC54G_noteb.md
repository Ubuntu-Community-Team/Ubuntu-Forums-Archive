---
title: "Dell inspiron 1100 Linksys Wireless-G WPC54G notebook adapter problem"
date: 2010-03-01
forum: Networking &amp; Wireless
---

### Post by Mokacoffay on 2010-03-01
Hello everyone, I am trying out Ubuntu for the very first time today and I cannot seem to get my wireless notebook card working. :???: Would anybody mind helping me out? I can't seem to detect my card at all (Fresh installation).  

Dell Inspiron 1100 
Linksys Wireless-G Notebook Adapter WPC54G ver. 3

Ubuntu 9.10

I was trying to follow the guidelines of [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

but I really have trouble sorting through all the feedback I get when using commands, Could someone help? 

-Sincerely, Ubuntu noobzor

---

### Post by chili555 on 2010-03-01
> I really have trouble sorting through all the feedback I get when using commands,You don't have to sort through it, we, who read and write this wonderful alien language called Ubuntu, will sort through it for you and help you get to the answer. When you enter the commands in a terminal, you can copy and paste the result to your posting reply. We will then interpret it and help you get connected.

---

### Post by Mokacoffay on 2010-03-01
> **chili555 said:**
> We will then interpret it and help you get connected.

Thanks! heres the feedback from the guidelines forum:

[B]Wireless Brand, Model and Wireless Chipset:
$ lspci[/B]

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 02)
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:04.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
03:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

**check interface:**
**$ ifconfig**

eth0      Link encap:Ethernet  HWaddr 00:0d:56:af:b9:ea  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:7 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

**$ iwconfig**

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

[B]Check for modules:
$ lsmod[/B]

Module                  Size  Used by
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
vfat                   10716  1 
nls_utf8                1568  1 
fat                    51452  1 vfat
isofs                  31620  1 
usb_storage            52544  2 
binfmt_misc             8356  1 
ppdev                   6688  0 
dell_wmi                2564  0 
joydev                 10272  0 
psmouse                56180  0 
serio_raw               5280  0 
arc4                    1660  2 
ecb                     2524  2 
snd_intel8x0           30168  2 
b43                   122136  0 
mac80211              181236  1 b43
cfg80211               93052  2 b43,mac80211
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
led_class               4096  1 b43
snd_pcm_oss            37920  0 
pcmcia                 36808  0 
snd_mixer_oss          16028  1 snd_pcm_oss
iptable_filter          3100  0 
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
yenta_socket           24200  2 
ip_tables              11692  1 iptable_filter
rsrc_nonstatic         11644  1 yenta_socket
snd_seq_dummy           2656  0 
x_tables               16544  1 ip_tables
lp                      8964  0 
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_seq_oss            28576  0 
dcdbas                  7292  0 
shpchp                 32272  0 
parport                35340  2 ppdev,lp
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
b44                    28684  0 
ssb                    35300  2 b43,b44
mii                     5212  1 b44
i915                  221064  2 
drm                   159584  2 i915
i2c_algo_bit            5760  1 i915
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video
[B]
 Kernel boot messages:
$ dmesg[/B]

[    0.573154] ACPI: Power Button [PBTN]
[    0.573240] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.573247] ACPI: Sleep Button [SBTN]
[    0.573805] processor LNXCPU:00: registered as cooling_device0
[    0.573815] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.579860] thermal LNXTHERM:01: registered as thermal_zone0
[    0.579881] ACPI: Thermal Zone [THM] (39 C)
[    0.608367] isapnp: Scanning for PnP cards...
[    0.700036] Switched to high resolution mode on CPU 0
[    0.880535] ACPI: Battery Slot [BAT0] (battery present)
[    0.967537] isapnp: No Plug & Play device found
[    0.970829] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.971766] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 7
[    0.971773] PCI: setting IRQ 7 as level-triggered
[    0.971781] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 7 (level, low) -> IRQ 7
[    0.971793] serial 0000:00:1f.6: PCI INT B disabled
[    0.973916] brd: module loaded
[    0.975060] loop: module loaded
[    0.975290] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.975543] ata_piix 0000:00:1f.1: version 2.13
[    0.975564] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    0.975577] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    0.975658] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.975854] scsi0 : ata_piix
[    0.976178] scsi1 : ata_piix
[    0.976481] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    0.976489] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    0.978619] Fixed MDIO Bus: probed
[    0.978715] PPP generic driver version 2.4.2
[    0.978984] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.979357] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    0.979368] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
[    0.979398] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.979404] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.979584] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.983512] ehci_hcd 0000:00:1d.7: debug port 1
[    0.983524] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    0.983947] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xf6f7fc00
[    0.996042] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.996248] usb usb1: configuration #1 chosen from 1 choice
[    0.996328] hub 1-0:1.0: USB hub found
[    0.996355] hub 1-0:1.0: 6 ports detected
[    0.996531] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.996593] uhci_hcd: USB Universal Host Controller Interface driver
[    0.996695] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    0.996716] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.996722] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.996844] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.996887] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80
[    0.997082] usb usb2: configuration #1 chosen from 1 choice
[    0.997174] hub 2-0:1.0: USB hub found
[    0.997207] hub 2-0:1.0: 2 ports detected
[    0.997676] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    0.997687] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.997706] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.997713] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.997860] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.997902] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000bf40
[    0.998109] usb usb3: configuration #1 chosen from 1 choice
[    0.998189] hub 3-0:1.0: USB hub found
[    0.998215] hub 3-0:1.0: 2 ports detected
[    0.998674] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    0.998684] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    0.998704] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.998711] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.998845] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.998887] uhci_hcd 0000:00:1d.2: irq 11, io base 0x0000bf20
[    0.999085] usb usb4: configuration #1 chosen from 1 choice
[    0.999169] hub 4-0:1.0: USB hub found
[    0.999202] hub 4-0:1.0: 2 ports detected
[    0.999443] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.999623] i8042.c: Warning: Keylock active.
[    1.002220] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.002235] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.002441] mice: PS/2 mouse device common for all mice
[    1.002844] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.002876] rtc0: alarms up to one day, 114 bytes nvram
[    1.003131] device-mapper: uevent: version 1.0.3
[    1.003433] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    1.003750] device-mapper: multipath: version 1.1.0 loaded
[    1.003757] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.004236] EISA: Probing bus 0 at eisa.0
[    1.004271] EISA: Detected 0 cards.
[    1.004452] cpuidle: using governor ladder
[    1.004457] cpuidle: using governor menu
[    1.005326] TCP cubic registered
[    1.005606] NET: Registered protocol family 10
[    1.006350] lo: Disabled Privacy Extensions
[    1.006816] NET: Registered protocol family 17
[    1.006881] Bluetooth: L2CAP ver 2.13
[    1.006885] Bluetooth: L2CAP socket layer initialized
[    1.006891] Bluetooth: SCO (Voice Link) ver 0.6
[    1.006894] Bluetooth: SCO socket layer initialized
[    1.007059] Bluetooth: RFCOMM TTY layer initialized
[    1.007068] Bluetooth: RFCOMM socket layer initialized
[    1.007072] Bluetooth: RFCOMM ver 1.11
[    1.007141] Using IPI No-Shortcut mode
[    1.007329] PM: Resume from disk failed.
[    1.007368] registered taskstats version 1
[    1.007554]   Magic number: 2:883:340
[    1.007677] rtc_cmos 00:06: setting system clock to 2010-07-24 17:19:01 UTC (1279991941)
[    1.007685] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.007688] EDD information not available.
[    1.008200] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.100065] hub 2-0:1.0: over-current change on port 1
[    1.144703] ata2.00: ATA-6: IC25N020ATMR04-0, MO1OAD0A, max UDMA/100
[    1.144709] ata2.00: 39070080 sectors, multi 8: LBA48 
[    1.160492] ata1.00: ATAPI: HL-DT-STCD-RW/DVD-ROM GCC-4240N, E112, max UDMA/33
[    1.160954] ata2.00: configured for UDMA/100
[    1.176254] ata1.00: configured for UDMA/33
[    1.181253] scsi 0:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4240N E112 PQ: 0 ANSI: 5
[    1.192382] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.192391] Uniform CD-ROM driver Revision: 3.20
[    1.192579] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.192723] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.192994] scsi 1:0:0:0: Direct-Access     ATA      IC25N020ATMR04-0 MO1O PQ: 0 ANSI: 5
[    1.193282] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.193452] sd 1:0:0:0: [sda] 39070080 512-byte logical blocks: (20.0 GB/18.6 GiB)
[    1.193686] sd 1:0:0:0: [sda] Write Protect is off
[    1.193693] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.193813] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.194383]  sda: sda1 sda2 < sda5 >
[    1.251059] sd 1:0:0:0: [sda] Attached SCSI disk
[    1.251094] Freeing unused kernel memory: 540k freed
[    1.252251] Write protecting the kernel text: 4568k
[    1.252291] Write protecting the kernel read-only data: 1836k
[    1.662157] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:20/input/input5
[    1.662256] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[    1.674496] Linux agpgart interface v0.103
[    1.739492] agpgart-intel 0000:00:00.0: Intel 830M Chipset
[    1.739669] agpgart-intel 0000:00:00.0: detected 892K stolen memory
[    1.742226] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe0000000
[    2.008278] [drm] Initialized drm 1.1.0 20060810
[    2.031695] i915 0000:00:02.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    2.031708] i915 0000:00:02.0: setting latency timer to 64
[    2.063862] b44 0000:02:01.0: PCI INT A -> Link[LNKB] -> GSI 7 (level, low) -> IRQ 7
[    2.178844] [drm] DAC-5: set mode 640x480 0
[    2.631672] ssb: Sonics Silicon Backplane found on PCI device 0000:02:01.0
[    2.631733] b44.c:v2.0
[    2.638795] i2c-adapter i2c-1: unable to read EDID block.
[    2.638808] i915 0000:00:02.0: LVDS-1: no EDID data
[    2.648168] [drm] fb0: inteldrmfb frame buffer device
[    2.648188] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    2.649598] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:0d:56:af:b9:ea
[    2.788600] render error detected, EIR: 0x00000010
[    2.788608] [drm:i915_handle_error] *ERROR* EIR stuck: 0x00000010, masking
[    2.788621] render error detected, EIR: 0x00000010
[    2.797269] [drm] LVDS-7: set mode 1024x768 a
[    2.959309] Console: switching to colour frame buffer device 128x48
[    3.585422] PM: Starting manual resume from disk
[    3.585433] PM: Resume from partition 8:5
[    3.585436] PM: Checking hibernation image.
[    3.585747] PM: Resume from disk failed.
[    3.593248] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    3.593259] EXT4-fs (sda1): write access will be enabled during recovery
[    3.612560] EXT4-fs (sda1): barriers enabled
[    5.311474] kjournald2 starting: pid 314, dev sda1:8, commit interval 5 seconds
[    5.311522] EXT4-fs (sda1): delayed allocation enabled
[    5.311528] EXT4-fs: file extents enabled
[    5.314188] EXT4-fs: mballoc enabled
[    5.314236] EXT4-fs (sda1): orphan cleanup on readonly fs
[    5.314271] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 135018
[    5.314486] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 135017
[    5.314536] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 135013
[    5.314581] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 135010
[    5.314620] EXT4-fs (sda1): 4 orphan inodes deleted
[    5.314628] EXT4-fs (sda1): recovery complete
[    5.655743] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    6.647721] type=1505 audit(1279991947.138:2): operation="profile_load" pid=337 name=/usr/share/gdm/guest-session/Xsession
[    6.653472] type=1505 audit(1279991947.144:3): operation="profile_load" pid=338 name=/sbin/dhclient3
[    6.654257] type=1505 audit(1279991947.144:4): operation="profile_load" pid=338 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    6.654686] type=1505 audit(1279991947.144:5): operation="profile_load" pid=338 name=/usr/lib/connman/scripts/dhclient-script
[    6.720311] type=1505 audit(1279991947.212:6): operation="profile_load" pid=339 name=/usr/bin/evince
[    6.732487] type=1505 audit(1279991947.224:7): operation="profile_load" pid=339 name=/usr/bin/evince-previewer
[    6.739856] type=1505 audit(1279991947.228:8): operation="profile_load" pid=339 name=/usr/bin/evince-thumbnailer
[    6.771996] type=1505 audit(1279991947.260:9): operation="profile_load" pid=341 name=/usr/lib/cups/backend/cups-pdf
[    6.773082] type=1505 audit(1279991947.264:10): operation="profile_load" pid=341 name=/usr/sbin/cupsd
[    6.795795] type=1505 audit(1279991947.284:11): operation="profile_load" pid=342 name=/usr/sbin/tcpdump
[    7.981650] Adding 730916k swap on /dev/sda5.  Priority:-1 extents:1 across:730916k 
[    8.412577] udev: starting version 147
[    8.520314] EXT4-fs (sda1): internal journal on sda1:8
[   11.888256] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.900912] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   11.920382] intel_rng: FWH not detected
[   12.383193] lp: driver loaded but no devices found
[   13.284155] ip_tables: (C) 2000-2006 Netfilter Core Team
[   13.718753] yenta_cardbus 0000:02:04.0: CardBus bridge found [1028:0149]
[   13.718779] yenta_cardbus 0000:02:04.0: Using CSCINT to route CSC interrupts to PCI
[   13.718783] yenta_cardbus 0000:02:04.0: Routing CardBus interrupts to PCI
[   13.718791] yenta_cardbus 0000:02:04.0: TI: mfunc 0x00001002, devctl 0x64
[   13.948693] yenta_cardbus 0000:02:04.0: ISA IRQ mask 0x0478, PCI irq 11
[   13.948701] yenta_cardbus 0000:02:04.0: Socket status: 30000020
[   13.948709] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   13.948726] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff
[   13.948732] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xd000-0xefff: clean.
[   13.949805] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge Memory window: 0xf8000000 - 0xfdffffff
[   13.949811] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge Memory window: 0x10000000 - 0x13ffffff
[   14.584059] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0
[   14.584103] pci 0000:03:00.0: reg 10 32bit mmio: [0x000000-0x001fff]
[   14.584372] b43-pci-bridge 0000:03:00.0: enabling device (0000 -> 0002)
[   14.584394] b43-pci-bridge 0000:03:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   14.584412] b43-pci-bridge 0000:03:00.0: setting latency timer to 64
[   14.648156] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[   14.863520] cfg80211: Calling CRDA to update world regulatory domain
[   15.027004] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   15.263811] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 7 (level, low) -> IRQ 7
[   15.263902] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   15.548895] phy0: Selected rate control algorithm 'minstrel'
[   15.550152] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
[   15.935263] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   15.936634] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   15.937241] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   15.937412] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   15.938399] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   16.088057] intel8x0_measure_ac97_clock: measured 55096 usecs (2655 samples)
[   16.088064] intel8x0: clocking to 48000
[   16.766778] cfg80211: World regulatory domain updated:
[   16.766788] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   16.766793] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.766798] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.766803] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.766808] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.766812] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.807656] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x254ab1, caps: 0x804713/0x0
[   16.850294] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[   16.897110] dell-wmi: No known WMI GUID found
[   18.125041] type=1505 audit(1280009958.616:12): operation="profile_replace" pid=789 name=/usr/share/gdm/guest-session/Xsession
[   18.129939] type=1505 audit(1280009958.620:13): operation="profile_replace" pid=790 name=/sbin/dhclient3
[   18.130748] type=1505 audit(1280009958.620:14): operation="profile_replace" pid=790 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   18.131221] type=1505 audit(1280009958.620:15): operation="profile_replace" pid=790 name=/usr/lib/connman/scripts/dhclient-script
[   18.144526] type=1505 audit(1280009958.636:16): operation="profile_replace" pid=791 name=/usr/bin/evince
[   18.202964] type=1505 audit(1280009958.692:17): operation="profile_replace" pid=791 name=/usr/bin/evince-previewer
[   18.219008] type=1505 audit(1280009958.708:18): operation="profile_replace" pid=791 name=/usr/bin/evince-thumbnailer
[   18.234040] type=1505 audit(1280009958.724:19): operation="profile_replace" pid=802 name=/usr/lib/cups/backend/cups-pdf
[   18.235161] type=1505 audit(1280009958.724:20): operation="profile_replace" pid=802 name=/usr/sbin/cupsd
[   18.241551] type=1505 audit(1280009958.732:21): operation="profile_replace" pid=803 name=/usr/sbin/tcpdump
[   20.367363] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.468107] b43 ssb1:0: firmware: requesting b43/ucode5.fw
[   20.555449] b43 ssb1:0: firmware: requesting b43-open/ucode5.fw
[   20.570591] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   20.570695] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   20.570782] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   22.516086] b43 ssb1:0: firmware: requesting b43/ucode5.fw
[   22.551832] b43 ssb1:0: firmware: requesting b43-open/ucode5.fw
[   22.592521] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   22.592622] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   22.592709] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   22.976386] ppdev: user-space parallel port driver
[   25.216027] i2c-adapter i2c-0: unable to read EDID block.
[   25.216038] i915 0000:00:02.0: VGA-1: no EDID data
[   25.226301] i2c-adapter i2c-0: unable to read EDID block.
[   25.226314] i915 0000:00:02.0: VGA-1: no EDID data
[   25.231907] i2c-adapter i2c-1: unable to read EDID block.
[   25.231919] i915 0000:00:02.0: LVDS-1: no EDID data
[   25.242425] i2c-adapter i2c-0: unable to read EDID block.
[   25.242435] i915 0000:00:02.0: VGA-1: no EDID data
[   25.252649] i2c-adapter i2c-0: unable to read EDID block.
[   25.252660] i915 0000:00:02.0: VGA-1: no EDID data
[   25.302800] i2c-adapter i2c-1: unable to read EDID block.
[   25.302812] i915 0000:00:02.0: LVDS-1: no EDID data
[   31.064004] i2c-adapter i2c-0: unable to read EDID block.
[   31.064050] i915 0000:00:02.0: VGA-1: no EDID data
[   31.074860] i2c-adapter i2c-0: unable to read EDID block.
[   31.074872] i915 0000:00:02.0: VGA-1: no EDID data
[   31.083220] i2c-adapter i2c-1: unable to read EDID block.
[   31.083230] i915 0000:00:02.0: LVDS-1: no EDID data
[   31.103837] i2c-adapter i2c-0: unable to read EDID block.
[   31.103847] i915 0000:00:02.0: VGA-1: no EDID data
[   31.115169] i2c-adapter i2c-0: unable to read EDID block.
[   31.115181] i915 0000:00:02.0: VGA-1: no EDID data
[   31.123671] i2c-adapter i2c-1: unable to read EDID block.
[   31.123683] i915 0000:00:02.0: LVDS-1: no EDID data
[   31.179969] i2c-adapter i2c-0: unable to read EDID block.
[   31.179979] i915 0000:00:02.0: VGA-1: no EDID data
[   31.189708] i2c-adapter i2c-0: unable to read EDID block.
[   31.189718] i915 0000:00:02.0: VGA-1: no EDID data
[   31.199625] i2c-adapter i2c-1: unable to read EDID block.
[   31.199636] i915 0000:00:02.0: LVDS-1: no EDID data
[   48.544265] i2c-adapter i2c-0: unable to read EDID block.
[   48.544276] i915 0000:00:02.0: VGA-1: no EDID data
[   48.554551] i2c-adapter i2c-0: unable to read EDID block.
[   48.554563] i915 0000:00:02.0: VGA-1: no EDID data
[   48.564199] i2c-adapter i2c-1: unable to read EDID block.
[   48.564210] i915 0000:00:02.0: LVDS-1: no EDID data
[   48.584704] i2c-adapter i2c-0: unable to read EDID block.
[   48.584714] i915 0000:00:02.0: VGA-1: no EDID data
[   48.594486] i2c-adapter i2c-0: unable to read EDID block.
[   48.594496] i915 0000:00:02.0: VGA-1: no EDID data
[   48.603998] i2c-adapter i2c-1: unable to read EDID block.
[   48.604043] i915 0000:00:02.0: LVDS-1: no EDID data
[   48.622572] i2c-adapter i2c-0: unable to read EDID block.
[   48.622581] i915 0000:00:02.0: VGA-1: no EDID data
[   48.633839] i2c-adapter i2c-0: unable to read EDID block.
[   48.633850] i915 0000:00:02.0: VGA-1: no EDID data
[   48.642423] i2c-adapter i2c-1: unable to read EDID block.
[   48.642435] i915 0000:00:02.0: LVDS-1: no EDID data
[ 1996.256073] b43 ssb1:0: firmware: requesting b43/ucode5.fw
[ 1996.838808] b43 ssb1:0: firmware: requesting b43-open/ucode5.fw
[ 1996.894992] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[ 1996.895002] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[ 1996.895007] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 2595.958263] i2c-adapter i2c-0: unable to read EDID block.
[ 2595.958273] i915 0000:00:02.0: VGA-1: no EDID data
[ 2595.967961] i2c-adapter i2c-0: unable to read EDID block.
[ 2595.967983] i915 0000:00:02.0: VGA-1: no EDID data
[ 2596.086649] i2c-adapter i2c-1: unable to read EDID block.
[ 2596.086659] i915 0000:00:02.0: LVDS-1: no EDID data
[ 2607.888761] i2c-adapter i2c-0: unable to read EDID block.
[ 2607.888771] i915 0000:00:02.0: VGA-1: no EDID data
[ 2607.898558] i2c-adapter i2c-0: unable to read EDID block.
[ 2607.898568] i915 0000:00:02.0: VGA-1: no EDID data
[ 2607.907115] i2c-adapter i2c-1: unable to read EDID block.
[ 2607.907125] i915 0000:00:02.0: LVDS-1: no EDID data
[ 3250.241417] pcmcia_socket pcmcia_socket0: pccard: card ejected from slot 0
[ 3250.532485] b43-pci-bridge 0000:03:00.0: PCI INT A disabled
[ 4129.200065] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0
[ 4129.200109] pci 0000:03:00.0: reg 10 32bit mmio: [0x000000-0x001fff]
[ 4129.200371] b43-pci-bridge 0000:03:00.0: enabling device (0000 -> 0002)
[ 4129.200391] b43-pci-bridge 0000:03:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[ 4129.200409] b43-pci-bridge 0000:03:00.0: setting latency timer to 64
[ 4129.240779] ssb: Failed to switch to core 0
[ 4129.241427] ssb: Failed to switch to core 0
[ 4129.242070] ssb: Failed to switch to core 0
[ 4129.242712] ssb: Failed to switch to core 0
[ 4129.242940] ssb: WARNING: Invalid SPROM CRC (corrupt SPROM)
[ 4129.242945] ssb: Unsupported SPROM  revision 255 detected. Will extract v1
[ 4129.243607] ssb: Failed to switch to core 2
[ 4129.243611] ssb: Backplane Revision 0xF0000000
[ 4129.243614] ------------[ cut here ]------------
[ 4129.243650] WARNING: at /build/buildd/linux-2.6.31/drivers/ssb/main.c:1041 ssb_tmslow_reject_bitmask+0x58/0x90 [ssb]()
[ 4129.243656] Hardware name: Inspiron 1100                   
[ 4129.243659] Modules linked in: binfmt_misc ppdev dell_wmi joydev psmouse serio_raw arc4 ecb snd_intel8x0 b43 mac80211 cfg80211 snd_ac97_codec ac97_bus led_class snd_pcm_oss pcmcia snd_mixer_oss iptable_filter snd_pcm yenta_socket ip_tables rsrc_nonstatic snd_seq_dummy x_tables lp pcmcia_core snd_seq_oss dcdbas shpchp parport snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore snd_page_alloc fbcon tileblit font bitblit softcursor b44 ssb mii i915 drm i2c_algo_bit intel_agp agpgart video output
[ 4129.243713] Pid: 630, comm: pccardd Tainted: G        W  2.6.31-14-generic #48-Ubuntu
[ 4129.243717] Call Trace:
[ 4129.243740]  [<c014518d>] warn_slowpath_common+0x6d/0xa0
[ 4129.243759]  [<d0722258>] ? ssb_tmslow_reject_bitmask+0x58/0x90 [ssb]
[ 4129.243777]  [<d0722258>] ? ssb_tmslow_reject_bitmask+0x58/0x90 [ssb]
[ 4129.243787]  [<c01451d5>] warn_slowpath_null+0x15/0x20
[ 4129.243805]  [<d0722258>] ssb_tmslow_reject_bitmask+0x58/0x90 [ssb]
[ 4129.243823]  [<d07222a4>] ssb_device_is_enabled+0x14/0x40 [ssb]
[ 4129.243843]  [<d07253fc>] ssb_pcicore_init+0x1c/0x70 [ssb]
[ 4129.243861]  [<d0721ea0>] ssb_attach_queued_buses+0xa0/0x100 [ssb]
[ 4129.243879]  [<d0722050>] ssb_bus_register+0x150/0x1c0 [ssb]
[ 4129.243896]  [<d0723770>] ? ssb_pci_get_invariants+0x0/0x80 [ssb]
[ 4129.243914]  [<d072213b>] ssb_bus_pcibus_register+0x2b/0x60 [ssb]
[ 4129.243933]  [<d0724088>] ssb_pcihost_probe+0x98/0x100 [ssb]
[ 4129.243945]  [<c032821e>] ? pci_match_device+0xbe/0xd0
[ 4129.243960]  [<c032804e>] local_pci_probe+0xe/0x10
[ 4129.243967]  [<c0328dd0>] pci_device_probe+0x60/0x80
[ 4129.243985]  [<c03a2960>] really_probe+0x50/0x140
[ 4129.243994]  [<c032821e>] ? pci_match_device+0xbe/0xd0
[ 4129.244069]  [<c03a2a69>] driver_probe_device+0x19/0x20
[ 4129.244077]  [<c03a2b31>] __device_attach+0x41/0x50
[ 4129.244083]  [<c03a1d18>] bus_for_each_drv+0x48/0x70
[ 4129.244089]  [<c03a2bdd>] device_attach+0x6d/0x80
[ 4129.244095]  [<c03a2af0>] ? __device_attach+0x0/0x50
[ 4129.244102]  [<c03a1b6d>] bus_probe_device+0x1d/0x40
[ 4129.244108]  [<c03a0782>] device_add+0x292/0x360
[ 4129.244115]  [<c0322025>] ? pci_bus_write_config_byte+0x55/0x70
[ 4129.244122]  [<c0322ba7>] pci_bus_add_device+0x17/0x40
[ 4129.244128]  [<c0322c10>] pci_bus_add_devices+0x40/0x120
[ 4129.244147]  [<d0bf7633>] cb_alloc+0xc3/0xda [pcmcia_core]
[ 4129.244164]  [<d0bf37b2>] socket_insert+0xd2/0x110 [pcmcia_core]
[ 4129.244180]  [<d0bf4149>] pccardd+0x1f9/0x280 [pcmcia_core]
[ 4129.244195]  [<d0bf3f50>] ? pccardd+0x0/0x280 [pcmcia_core]
[ 4129.244204]  [<c015bf8c>] kthread+0x7c/0x90
[ 4129.244211]  [<c015bf10>] ? kthread+0x0/0x90
[ 4129.244218]  [<c0104007>] kernel_thread_helper+0x7/0x10
[ 4129.244224] ---[ end trace a7919e7f17c0a727 ]---
[ 4129.244871] ssb: Failed to switch to core 2
[ 4129.245514] ssb: Failed to switch to core 2
[ 4129.246156] ssb: Failed to switch to core 2
[ 4129.246797] ssb: Failed to switch to core 2
[ 4129.247440] ssb: Failed to switch to core 2
[ 4129.248037] ssb: Failed to switch to core 2
[ 4129.248757] ssb: Failed to switch to core 2
[ 4129.249399] ssb: Failed to switch to core 2
[ 4129.250041] ssb: Failed to switch to core 2
[ 4129.250683] ssb: Failed to switch to core 2
[ 4129.251326] ssb: Failed to switch to core 2
[ 4129.251967] ssb: Failed to switch to core 2
[ 4129.252102] ssb: Failed to switch to core 2
[ 4129.267164] b43-phy1: Broadcom 4318 WLAN found (core revision 9)
[ 4129.267830] ssb: Failed to switch to core 1
[ 4129.268024] ssb: Failed to switch to core 1
[ 4129.269180] ssb: Failed to switch to core 1
[ 4129.269823] ssb: Failed to switch to core 1
[ 4129.270466] ssb: Failed to switch to core 1
[ 4129.271108] ssb: Failed to switch to core 1
[ 4129.271750] ssb: Failed to switch to core 1
[ 4129.272391] ssb: Failed to switch to core 1
[ 4129.273064] ssb: Failed to switch to core 1
[ 4129.273706] ssb: Failed to switch to core 1
[ 4129.274349] ssb: Failed to switch to core 1
[ 4129.274991] ssb: Failed to switch to core 1
[ 4129.280684] ssb: Failed to switch to core 1
[ 4129.281329] ssb: Failed to switch to core 1
[ 4129.281970] ssb: Failed to switch to core 1
[ 4129.288674] ssb: Failed to switch to core 1
[ 4129.289318] ssb: Failed to switch to core 1
[ 4129.296687] ssb: Failed to switch to core 1
[ 4129.297334] ssb: Failed to switch to core 1
[ 4129.297985] ssb: Failed to switch to core 1
[ 4129.298068] b43-phy1 ERROR: FOUND UNSUPPORTED PHY (Analog 15, Type 15, Revision 255)
[ 4129.298114] b43: probe of ssb2:0 failed with error -95
[ 4129.298129] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[ 4304.896057] usb 1-3: new high speed USB device using ehci_hcd and address 2
[ 4305.029122] usb 1-3: configuration #1 chosen from 1 choice
[ 4305.238641] Initializing USB Mass Storage driver...
[ 4305.241654] scsi2 : SCSI emulation for USB Mass Storage devices
[ 4305.242253] usbcore: registered new interface driver usb-storage
[ 4305.242265] USB Mass Storage support registered.
[ 4305.243990] usb-storage: device found at 2
[ 4305.243996] usb-storage: waiting for device to settle before scanning
[ 4310.240316] usb-storage: device scan complete
[ 4310.240892] scsi 2:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  8.02 PQ: 0 ANSI: 0 CCS
[ 4310.241386] scsi 2:0:0:1: CD-ROM            SanDisk  U3 Cruzer Micro  8.02 PQ: 0 ANSI: 0
[ 4310.242893] sd 2:0:0:0: Attached scsi generic sg2 type 0
[ 4310.272916] sd 2:0:0:0: [sdb] 3915775 512-byte logical blocks: (2.00 GB/1.86 GiB)
[ 4310.275820] sr1: scsi3-mmc drive: 48x/48x tray
[ 4310.276226] sr 2:0:0:1: Attached scsi CD-ROM sr1
[ 4310.276434] sr 2:0:0:1: Attached scsi generic sg3 type 5
[ 4310.277960] sd 2:0:0:0: [sdb] Write Protect is off
[ 4310.277970] sd 2:0:0:0: [sdb] Mode Sense: 45 00 00 08
[ 4310.277975] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 4310.288862] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 4310.288879]  sdb: sdb1
[ 4310.297347] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 4310.297360] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[ 4312.511088] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 4312.563374] ISOFS: changing to secondary root
[ 4720.508488] pcmcia_socket pcmcia_socket0: pccard: card ejected from slot 0
[ 4720.544327] b43-pci-bridge 0000:03:00.0: PCI INT A disabled
[ 4752.352064] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0
[ 4752.352110] pci 0000:03:00.0: reg 10 32bit mmio: [0x000000-0x001fff]
[ 4752.352377] b43-pci-bridge 0000:03:00.0: enabling device (0000 -> 0002)
[ 4752.352398] b43-pci-bridge 0000:03:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[ 4752.352416] b43-pci-bridge 0000:03:00.0: setting latency timer to 64
[ 4752.412189] b43-phy2: Broadcom 4318 WLAN found (core revision 9)
[ 4752.486296] phy2: Selected rate control algorithm 'minstrel'
[ 4752.487499] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[ 4752.840094] b43 ssb3:0: firmware: requesting b43/ucode5.fw
[ 4753.127336] b43 ssb3:0: firmware: requesting b43-open/ucode5.fw
[ 4753.141790] b43-phy2 ERROR: Firmware file "b43/ucode5.fw" not found
[ 4753.141800] b43-phy2 ERROR: Firmware file "b43-open/ucode5.fw" not found
[ 4753.141806] b43-phy2 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 4753.392086] b43 ssb3:0: firmware: requesting b43/ucode5.fw
[ 4753.406678] b43 ssb3:0: firmware: requesting b43-open/ucode5.fw
[ 4753.443196] b43-phy2 ERROR: Firmware file "b43/ucode5.fw" not found
[ 4753.443206] b43-phy2 ERROR: Firmware file "b43-open/ucode5.fw" not found
[ 4753.443211] b43-phy2 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 4802.467681] pcmcia_socket pcmcia_socket0: pccard: card ejected from slot 0
[ 4802.756535] b43-pci-bridge 0000:03:00.0: PCI INT A disabled
[ 4813.280085] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0
[ 4813.280130] pci 0000:03:00.0: reg 10 32bit mmio: [0x000000-0x001fff]
[ 4813.280398] b43-pci-bridge 0000:03:00.0: enabling device (0000 -> 0002)
[ 4813.280420] b43-pci-bridge 0000:03:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[ 4813.280438] b43-pci-bridge 0000:03:00.0: setting latency timer to 64
[ 4813.340213] b43-phy3: Broadcom 4318 WLAN found (core revision 9)
[ 4813.409160] phy3: Selected rate control algorithm 'minstrel'
[ 4813.442221] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[ 4813.524068] b43 ssb4:0: firmware: requesting b43/ucode5.fw
[ 4813.535513] b43 ssb4:0: firmware: requesting b43-open/ucode5.fw
[ 4813.557570] b43-phy3 ERROR: Firmware file "b43/ucode5.fw" not found
[ 4813.557580] b43-phy3 ERROR: Firmware file "b43-open/ucode5.fw" not found
[ 4813.557586] b43-phy3 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 4813.589622] b43 ssb4:0: firmware: requesting b43/ucode5.fw
[ 4813.635276] b43 ssb4:0: firmware: requesting b43-open/ucode5.fw
[ 4813.659127] b43-phy3 ERROR: Firmware file "b43/ucode5.fw" not found
[ 4813.659138] b43-phy3 ERROR: Firmware file "b43-open/ucode5.fw" not found
[ 4813.659143] b43-phy3 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 4827.246845] pcmcia_socket pcmcia_socket0: pccard: card ejected from slot 0
[ 4827.536516] b43-pci-bridge 0000:03:00.0: PCI INT A disabled
[ 5800.836058] pcmcia_socket pcmcia_socket0: cs: unable to apply power.
[ 5801.612102] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0
[ 5801.612147] pci 0000:03:00.0: reg 10 32bit mmio: [0x000000-0x001fff]
[ 5801.612413] b43-pci-bridge 0000:03:00.0: enabling device (0000 -> 0002)
[ 5801.612434] b43-pci-bridge 0000:03:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[ 5801.612453] b43-pci-bridge 0000:03:00.0: setting latency timer to 64
[ 5801.672193] b43-phy4: Broadcom 4318 WLAN found (core revision 9)
[ 5801.741152] phy4: Selected rate control algorithm 'minstrel'
[ 5801.742357] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[ 5801.832075] b43 ssb5:0: firmware: requesting b43/ucode5.fw
[ 5801.854732] b43 ssb5:0: firmware: requesting b43-open/ucode5.fw
[ 5801.875438] b43-phy4 ERROR: Firmware file "b43/ucode5.fw" not found
[ 5801.875448] b43-phy4 ERROR: Firmware file "b43-open/ucode5.fw" not found
[ 5801.875453] b43-phy4 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 5801.923504] b43 ssb5:0: firmware: requesting b43/ucode5.fw
[ 5801.946122] b43 ssb5:0: firmware: requesting b43-open/ucode5.fw
[ 5801.967070] b43-phy4 ERROR: Firmware file "b43/ucode5.fw" not found
[ 5801.967082] b43-phy4 ERROR: Firmware file "b43-open/ucode5.fw" not found
[ 5801.967087] b43-phy4 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.

[B] Network configuration:
$ sudo lshw -C network[/B]

*-network               
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:af:b9:ea
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=32 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: irq:7 memory:fcffe000-fcffffff
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:11 memory:f8000000-f8001fff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:bf:49:7f:b7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

[B]Scan for networks:
$ iwlist scan[/B]

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

[B] Ubuntu Version: 
$ lsb_release -d[/B]

9.10

[B]Kernel/architecture (including 32 vs. 64 bit): 
$ uname -mr[/B]
2.6.31 - 14 - generic i686

Sorry about the spam, I hope this helps in finding a solution and make ubuntu enjoyable :D
Edit: fixed bolds

---

### Post by chili555 on 2010-03-01
> [ 20.555449] b43 ssb1:0: firmware: requesting b43-open/ucode5.fw
[ 20.570591] b43-phy0 ERROR: [COLOR="Red"]Firmware file "b43/ucode5.fw" not found[/COLOR]
[ 20.570695] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[ 20.570782] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/...devicefirmware](http://wireless.kernel.org/en/users/...devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.Can you hook up an ethernet cable and get connected so we can download files? If so, we can solve this quickly and easily.

---

### Post by Mokacoffay on 2010-03-01
Yeah I have a jump drive that I've been switching back and forth in order to post those copypastas. I need to download a "b43/ucode5.fw" from that website, correct?

---

### Post by chili555 on 2010-03-01
You need b43-fwcutter from here: [http://packages.ubuntu.com/karmic/b43-fwcutter](http://packages.ubuntu.com/karmic/b43-fwcutter)

From the website referenced, you need this: [http://downloads.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)

Then open a terminal and do:```
sudo dpkg -i b43-fwcutter*
tar xjf broadcom-wl-4.150.10.5.tar.bz2
cd broadcom-wl-4.150.10.5/driver
sudo b43-fwcutter -w /lib/firmware/ wl_apsta_mimo.o
```Reboot. Your wireless should spring to life.

Post back if you get stuck.

---

### Post by Mokacoffay on 2010-03-01
Thanks a ton! I'll give it a shot.  This whole thing is still pretty new to me.

---

### Post by Mokacoffay on 2010-03-01
Thank you very much! My card seems to be working now :D +9001 rep to the casual ubuntu forum support roamers!

---

### Post by chili555 on 2010-03-02
> +9001 rep to the casual ubuntu forum support roamers!I will take that as a very much appreciated compliment. Thanks!

I'm glad it's working for you.

---

### Post by dwpbike on 2010-09-05
and i've got to give you credit for making me realize i already had generic drivers in the same scenario.  competing drivers was the real symptom and blacklist was the solution.  many tanks.

---

### Post by n7gtb on 2010-12-26
Does anyone here happen to know if this is still an issue with the latest (stable) version of Ubuntu?  I just acquired an Inspiron 1100 from a local computer shop and plan to use it at night class, it currently has XP sp3....

Thanks,
-Vern

---

### Post by n7gtb on 2010-12-26
Answered my own question...  While it doesn't 'just work' out of the box, much of the work has been done.  There is a utility that notifies you that certain drivers are not open source but proprietary and gives you the option of installing or no...  I gave it permission and the b43 stuff was onboard and working.  I configured the linksys card, installed the key and viola!  The laptop is now wireless...  :)

---

### Post by n7gtb on 2010-12-27
> **n7gtb said:**
> Answered my own question...  While it doesn't 'just work' out of the box, much of the work has been done.  There is a utility that notifies you that certain drivers are not open source but proprietary and gives you the option of installing or no...  I gave it permission and the b43 stuff was onboard and working.  I configured the linksys card, installed the key and viola!  The laptop is now wireless...  :)

After using this for a day, I can say that the Inspiron 1100 with Linksys card now performs much better than it did under XP!  The laptop runs much cooler, the fan runs less often.  The wireless 'dead zone' that exists in my house was off limits (except via hardline) if I needed the web.  The signal is still weak, but Ubuntu handles it well...

---

### Post by ShirakoDX on 2012-09-02
> **chili555 said:**
> You need b43-fwcutter from here: [http://packages.ubuntu.com/karmic/b43-fwcutter](http://packages.ubuntu.com/karmic/b43-fwcutter)

From the website referenced, you need this: [http://downloads.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)

Then open a terminal and do:```
sudo dpkg -i b43-fwcutter*
tar xjf broadcom-wl-4.150.10.5.tar.bz2
cd broadcom-wl-4.150.10.5/driver
sudo b43-fwcutter -w /lib/firmware/ wl_apsta_mimo.o
```Reboot. Your wireless should spring to life.

Post back if you get stuck.

Hello. I have been fighting with my linksys wpc54g version 3.1 for a while now...Nothing I do seems to work. I have followed many guides but because I know nothing about how ubuntu works, I really cannot troubleshoot the problem. Right now, when i click the button on the top bar to see my connections, wireless states the device is not ready(Firmware missing) It remains this way no matter what I do...I am running ubuntu 11.04 off of an 8 gig USB 2.0 thumb drive. I have the wireless cards CD, I have several other jump drives as well. I have enjoyed ubuntu before on my other laptop, which it detected the internal wireless card right from the start with. This one I believe also has an internal wireless card(I see it when I take it apart..or so I believe it is the wireless) But I have no clue what it is, XP does not detect it, nor does Ubuntu and there really is little information about my computer (Northgate 755118. I believe it is an X-book) northgate had gone out of business several years ago, and I really don't care toward getting the internal card working because I have the PCI card. I tried following your post here, however I get this: 
shirakodx@shirakodx-laptop:~$ sudo dpkg -i b43-fwcutter*
[sudo] password for shirakodx: 
dpkg: error processing b43-fwcutter* (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 b43-fwcutter*
shirakodx@shirakodx-laptop:~$ 
 Do I need to move the archive to a certain spot? If so, where? Right now it is in my downloads folder, if that helps. I believe I have B43-fwcutter installed already..but am not for sure.


EDIT! Nevermind, I just had to extract the archive myself, then I was able to get it working.

---

