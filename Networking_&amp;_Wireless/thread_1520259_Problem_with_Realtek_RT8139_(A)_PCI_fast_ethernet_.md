---
title: "Problem with Realtek RT8139 (A) PCI fast ethernet adapter"
date: 2010-06-29
forum: Networking &amp; Wireless
---

### Post by murox on 2010-06-29
A newcomer to Ubuntu and  novice generally I need some help to get a wireless connection on a Desktop medion- model PC MT7 - type MED MT 345, now running Ubuntu 10.04 LTS. Previously ran windows xp pro with no problems on wireless. Do  I have an issue with the **Realtek RT8139 (A) PCI fast ethernet adapter**                          wireless function ?
The wireless connection shows as disabled , is greyed out and I cannot find a way of enabling it. The wired side of things works perfectly. Below are the results of various commands, this does make a long post, but I have tried to follow the directions for posting here. Thanks in advance.
 **uname -mr**
2.6.32-22-generic i686

** lsusb**
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 003 Device 002: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 19b6:8192 Infotech Logistic, LLC 
Bus 001 Device 008: ID 0db0:4023 Micro Star International 
Bus 001 Device 007: ID 0bc7:0006 X10 Wireless Technology, Inc. Wireless Transceiver (ACPI-compliant)
Bus 001 Device 006: ID 0db0:6855 Micro Star International Bluetooth Device
Bus 001 Device 005: ID 148f:2570 Ralink Technology, Corp. 802.11g WiFi
Bus 001 Device 004: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub [ednet]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

**lspci**
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)] (Secondary)
03:01.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
03:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
03:04.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
03:06.0 Ethernet controller: VIA Technologies, Inc. VT6105/VT6106S [Rhine-III] (rev 8b)

**  lsmod**
Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8901  1 
fat                    47767  1 vfat
rfcomm                 33421  4 
binfmt_misc             6587  1 
tda1004x               15070  0 
saa7134_dvb            22167  0 
videobuf_dvb            5175  1 saa7134_dvb
dvb_core               86142  1 videobuf_dvb
saa7134_alsa           10380  1 
sco                     7885  2 
bridge                 45582  0 
stp                     1655  1 bridge
bnep                    9436  2 
tuner_simple           13577  1 
tuner_types            14233  1 tuner_simple
l2cap                  30624  16 rfcomm,bnep
tea5767                 5950  0 
tda9887                 9589  1 
snd_hda_codec_cmedia     7454  1 
tda8290                12092  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_hda_intel          21877  2 
vga16fb                11385  0 
arc4                    1153  2 
vgastate                8961  1 vga16fb
tuner                  20412  2 
snd_hda_codec          74201  2 snd_hda_codec_cmedia,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  4 saa7134_alsa,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
rt2500usb              18141  0 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
saa7134               143391  2 saa7134_dvb,saa7134_alsa
rt2x00usb               9703  1 rt2500usb
snd_timer              19098  2 snd_pcm,snd_seq
rt2x00lib              27509  2 rt2500usb,rt2x00usb
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
led_class               2864  1 rt2x00lib
radeon                674135  3 
ir_common              38875  1 saa7134
v4l2_common            15431  2 tuner,saa7134
lirc_atiusb            13388  0 
lirc_dev                8884  1 lirc_atiusb
ttm                    49943  1 radeon
snd                    54148  18 saa7134_alsa,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               34361  3 tuner,saa7134,v4l2_common
v4l1_compat            13251  1 videodev
videobuf_dma_sg        10782  3 saa7134_dvb,saa7134_alsa,saa7134
mac80211              204922  2 rt2x00usb,rt2x00lib
psmouse                63245  0 
ppdev                   5259  0 
drm_kms_helper         29297  1 radeon
intel_agp              24177  0 
cfg80211              126485  2 rt2x00lib,mac80211
usb_storage            39425  1 
ati_remote              8087  0 
btusb                  10925  2 
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
serio_raw               3978  0 
usbhid                 36110  0 
hid                    67032  1 usbhid
parport_pc             25962  1 
videobuf_core          16356  3 videobuf_dvb,saa7134,videobuf_dma_sg
tveeprom               11102  1 saa7134
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
drm                   162471  5 radeon,ttm,drm_kms_helper
agpgart                31724  3 ttm,intel_agp,drm
i2c_algo_bit            5028  1 radeon
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
ohci1394               26950  0 
floppy                 53016  0 
via_rhine              19154  0 
mii                     4381  1 via_rhine
ieee1394               81181  1 ohci1394

**sudo lshw -C network**
[sudo] password for murray: 
  *-network               
       description: Ethernet interface
       product: VT6105/VT6106S [Rhine-III]
       vendor: VIA Technologies, Inc.
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: eth0
       version: 8b
       serial: 00:11:09:bd:81:48
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=32 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10MB/s
       resources: irq:18 ioport:d300(size=256) memory:d8003000-d80030ff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:11:09:e0:e5:a3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg


**iwlist scan**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

pan0      Interface doesn't support scanning.

 ** iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSIDff/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thrff   Fragment thrff
          Power Managementn
          
pan0      no wireless extensions.



 ** ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:11:09:bd:81:48  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

**dmesg**

[    0.296798] pci 0000:01:00.0: Boot video device
[    0.297113] cpufreq-nforce2: No nForce2 chipset.
[    0.297162] Scanning for low memory corruption every 60 seconds
[    0.297334] audit: initializing netlink socket (disabled)
[    0.297350] type=2000 audit(1277817077.294:1): initialized
[    0.308642] highmem bounce pool size: 64 pages
[    0.308655] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.311460] VFS: Disk quotas dquot_6.5.2
[    0.311576] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.312699] fuse init (API version 7.13)
[    0.312858] msgmni has been set to 1716
[    0.313226] alg: No test for stdrng (krng)
[    0.313324] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.313330] io scheduler noop registered
[    0.313333] io scheduler anticipatory registered
[    0.313337] io scheduler deadline registered
[    0.313412] io scheduler cfq registered (default)
[    0.313637]   alloc irq_desc for 24 on node -1
[    0.313641]   alloc kstat_irqs on node -1
[    0.313654] pcieport 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.313664] pcieport 0000:00:01.0: setting latency timer to 64
[    0.313810]   alloc irq_desc for 25 on node -1
[    0.313814]   alloc kstat_irqs on node -1
[    0.313825] pcieport 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.313836] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.313981] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.314082] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.314249] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.314256] ACPI: Power Button [PWRB]
[    0.314356] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.314362] ACPI: Sleep Button [SLPB]
[    0.314462] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.314467] ACPI: Power Button [PWRF]
[    0.314548] fan PNP0C0B:00: registered as cooling_device0
[    0.314558] ACPI: Fan [FAN] (on)
[    0.314973] processor LNXCPU:00: registered as cooling_device1
[    0.315277] ACPI: SSDT 3fff7d00 00087 (v01  PmRef  Cpu1Ist 00003000 INTL 20041203)
[    0.315596] processor LNXCPU:01: registered as cooling_device2
[    0.320524] thermal LNXTHERM:01: registered as thermal_zone0
[    0.320539] ACPI: Thermal Zone [THRM] (50 C)
[    0.323351] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.323471] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.323988] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.326029] brd: module loaded
[    0.326662] isapnp: Scanning for PnP cards...
[    0.326928] loop: module loaded
[    0.327057] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.327190] ata_piix 0000:00:1f.1: version 2.13
[    0.327208]   alloc irq_desc for 18 on node -1
[    0.327212]   alloc kstat_irqs on node -1
[    0.327221] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.327270] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.327366] scsi0 : ata_piix
[    0.327485] scsi1 : ata_piix
[    0.328590] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    0.328595] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    0.328625]   alloc irq_desc for 19 on node -1
[    0.328629]   alloc kstat_irqs on node -1
[    0.328636] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.328643] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.328689] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.328753] scsi2 : ata_piix
[    0.328838] scsi3 : ata_piix
[    0.329914] ata3: SATA max UDMA/133 cmd 0xe400 ctl 0xe500 bmdma 0xe800 irq 19
[    0.329920] ata4: SATA max UDMA/133 cmd 0xe600 ctl 0xe700 bmdma 0xe808 irq 19
[    0.330520] Fixed MDIO Bus: probed
[    0.330580] PPP generic driver version 2.4.2
[    0.330639] tun: Universal TUN/TAP device driver, 1.6
[    0.330643] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.330778] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.330804]   alloc irq_desc for 23 on node -1
[    0.330808]   alloc kstat_irqs on node -1
[    0.330815] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.330833] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.330838] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.330890] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.334794] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    0.334840] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd8104000
[    0.338936] ata2: port disabled. ignoring.
[    0.350466] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.350629] usb usb1: configuration #1 chosen from 1 choice
[    0.350679] hub 1-0:1.0: USB hub found
[    0.350692] hub 1-0:1.0: 8 ports detected
[    0.350793] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.350823] uhci_hcd: USB Universal Host Controller Interface driver
[    0.350869] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.350879] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.350884] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.350939] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.350968] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000e300
[    0.351106] usb usb2: configuration #1 chosen from 1 choice
[    0.351150] hub 2-0:1.0: USB hub found
[    0.351163] hub 2-0:1.0: 2 ports detected
[    0.351235] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.351244] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.351249] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.351302] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.351329] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e000
[    0.351471] usb usb3: configuration #1 chosen from 1 choice
[    0.351514] hub 3-0:1.0: USB hub found
[    0.351524] hub 3-0:1.0: 2 ports detected
[    0.351591] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.351600] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.351605] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.351662] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.351699] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e100
[    0.351840] usb usb4: configuration #1 chosen from 1 choice
[    0.351886] hub 4-0:1.0: USB hub found
[    0.351895] hub 4-0:1.0: 2 ports detected
[    0.351963] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.351971] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.351976] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.352025] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.352060] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000e200
[    0.352193] usb usb5: configuration #1 chosen from 1 choice
[    0.352238] hub 5-0:1.0: USB hub found
[    0.352249] hub 5-0:1.0: 2 ports detected
[    0.352407] PNP: No PS/2 controller found. Probing ports directly.
[    0.359289] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.359299] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.359508] mice: PS/2 mouse device common for all mice
[    0.359714] rtc_cmos 00:03: RTC can wake from S4
[    0.359775] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.359804] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.359980] device-mapper: uevent: version 1.0.3
[    0.382514] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.422758] device-mapper: multipath: version 1.1.0 loaded
[    0.422764] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.469568] EISA: Probing bus 0 at eisa.0
[    0.469577] Cannot allocate resource for EISA slot 1
[    0.469604] EISA: Detected 0 cards.
[    0.504621] ata3.00: ATA-6: WDC WD1600JD-00HBB0, 08.02D08, max UDMA/133
[    0.504627] ata3.00: 312581808 sectors, multi 16: LBA48 
[    0.504726] ata4.00: ATA-6: WDC WD1600JD-22HBB0, 08.02D08, max UDMA/133
[    0.504731] ata4.00: 312581808 sectors, multi 16: LBA48 
[    0.505280] Freeing initrd memory: 7779k freed
[    0.509283] cpuidle: using governor ladder
[    0.509287] cpuidle: using governor menu
[    0.510074] TCP cubic registered
[    0.510297] NET: Registered protocol family 10
[    0.511106] lo: Disabled Privacy Extensions
[    0.511685] NET: Registered protocol family 17
[    0.512611] Using IPI No-Shortcut mode
[    0.512758] PM: Resume from disk failed.
[    0.512776] registered taskstats version 1
[    0.513179]   Magic number: 14:174:181
[    0.513281] rtc_cmos 00:03: setting system clock to 2010-06-29 13:11:18 UTC (127781707
[    0.513286] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.513289] EDD information not available.
[    0.513777] ata1.00: ATAPI: PIONEER DVD RW  DVR-109, 1.09, max UDMA/33
[    0.513832] ata1.01: ATAPI: HL-DT-STDVD-ROM GDR8163B, 0L23, max UDMA/33
[    0.519159] ata1.00: configured for UDMA/33
[    0.520345] ata3.00: configured for UDMA/133
[    0.520399] ata4.00: configured for UDMA/133
[    0.534572] ata1.01: configured for UDMA/33
[    0.686975] isapnp: No Plug & Play device found
[    0.688648] scsi 0:0:0:0: CD-ROM            PIONEER  DVD RW  DVR-109  1.09 PQ: 0 ANSI: 5
[    0.695602] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    0.695607] Uniform CD-ROM driver Revision: 3.20
[    0.695738] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    0.695805] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    0.703961] scsi 0:0:1:0: CD-ROM            HL-DT-ST DVD-ROM GDR8163B 0L23 PQ: 0 ANSI: 5
[    0.711267] sr1: scsi3-mmc drive: 52x/52x cd/rw xa/form2 cdda tray
[    0.711373] sr 0:0:1:0: Attached scsi CD-ROM sr1
[    0.711430] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    0.711603] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1600JD-00H 08.0 PQ: 0 ANSI: 5
[    0.711762] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    0.711793] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    0.711860] sd 2:0:0:0: [sda] Write Protect is off
[    0.711866] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.711972] scsi 3:0:0:0: Direct-Access     ATA      WDC WD1600JD-22H 08.0 PQ: 0 ANSI: 5
[    0.712116] sd 3:0:0:0: [sdb] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    0.712150] sd 3:0:0:0: Attached scsi generic sg3 type 0
[    0.712213] sd 3:0:0:0: [sdb] Write Protect is off
[    0.712219] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    0.712257] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.712274] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.712563]  sda:
[    0.712669]  sdb: sda1 sda2 < sdb1 < sdb5 >
[    0.738209] sd 3:0:0:0: [sdb] Attached SCSI disk
[    0.746577]  sda5 >
[    0.746916] sd 2:0:0:0: [sda] Attached SCSI disk
[    0.746932] Freeing unused kernel memory: 656k freed
[    0.747390] Write protecting the kernel text: 4676k
[    0.747441] Write protecting the kernel read-only data: 1840k
[    0.769221] udev: starting version 151
[    0.774705] usb 1-6: new high speed USB device using ehci_hcd and address 4
[    0.908609] usb 1-6: configuration #1 chosen from 1 choice
[    0.908899] hub 1-6:1.0: USB hub found
[    0.909216] hub 1-6:1.0: 4 ports detected
[    0.988346] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    0.988354] via-rhine: Broken BIOS detected, avoid_D3 enabled.
[    0.988405] via-rhine 0000:03:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.994986] eth0: VIA Rhine III at 0xd8003000, 00:11:09:bd:81:48, IRQ 18.
[    0.995724] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[    1.001432] ohci1394 0000:03:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.018376] FDC 0 is a post-1991 82077
[    1.060914] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[d8001000-d80017ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    1.150884] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    1.154960] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    1.334633] usb 3-1: configuration #1 chosen from 1 choice
[    1.576657] usb 3-2: new low speed USB device using uhci_hcd and address 3
[    1.750693] usb 3-2: configuration #1 chosen from 1 choice
[    1.824358] usb 1-6.1: new high speed USB device using ehci_hcd and address 5
[    2.051258] usb 1-6.1: configuration #1 chosen from 1 choice
[    2.124275] usb 1-6.2: new full speed USB device using ehci_hcd and address 6
[    2.218270] usb 1-6.2: configuration #1 chosen from 1 choice
[    2.288299] usb 1-6.3: new low speed USB device using ehci_hcd and address 7
[    2.336261] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc00008e66a5]
[    2.385167] usb 1-6.3: configuration #1 chosen from 1 choice
[    2.456321] usb 1-6.4: new high speed USB device using ehci_hcd and address 8
[    2.550570] usb 1-6.4: configuration #1 chosen from 1 choice
[   11.137751] udev: starting version 151
[   11.150382] Adding 3004408k swap on /dev/sda5.  Priority:-1 extents:1 across:3004408k 
[   11.290377] lp: driver loaded but no devices found
[   11.495531] Linux agpgart interface v0.103
[   11.537243] intel_rng: FWH not detected
[   11.617217] [drm] Initialized drm 1.1.0 20060810
[   11.638913] parport_pc 00:08: reported by Plug and Play ACPI
[   11.638974] parport0: PC-style at 0x378 (0x77, irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   11.649147] type=1505 audit(1277809889.634:2):  operation="profile_load" pid=564 name="/sbin/dhclient3"
[   11.649920] type=1505 audit(1277809889.634:3):  operation="profile_load" pid=564 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   11.650337] type=1505 audit(1277809889.634:4):  operation="profile_load" pid=564 name="/usr/lib/connman/scripts/dhclient-script"
[   11.658824] usbcore: registered new interface driver hiddev
[   11.675365] input: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input4
[   11.675549] generic-usb 0003:045E:0039.0001: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.1-1/input0
[   11.677404] Bluetooth: Core ver 2.15
[   11.683667] NET: Registered protocol family 31
[   11.683672] Bluetooth: HCI device and connection manager initialized
[   11.683677] Bluetooth: HCI socket layer initialized
[   11.690399] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input5
[   11.690538] generic-usb 0003:413C:2003.0002: input,hidraw1: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1d.1-2/input0
[   11.690588] usbcore: registered new interface driver usbhid
[   11.690594] usbhid: v2.6:USB HID core driver
[   11.696081] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   11.696470] usbcore: registered new interface driver btusb
[   11.727733] Initializing USB Mass Storage driver...
[   11.727944] scsi4 : SCSI emulation for USB Mass Storage devices
[   11.728303] lp0: using parport0 (interrupt-driven).
[   11.728311] usbcore: registered new interface driver usb-storage
[   11.728318] USB Mass Storage support registered.
[   11.730585] usb-storage: device found at 8
[   11.730590] usb-storage: waiting for device to settle before scanning
[   11.734689] input: X10 Wireless Technology Inc USB Receiver as /devices/pci0000:00/0000:00:1d.7/usb1/1-6/1-6.3/input/input6
[   11.734887] usbcore: registered new interface driver ati_remote
[   11.734895] ati_remote: 2.2.1:ATI/X10 RF USB Remote Control
[   11.735543] usb 1-6.3: Weird data, len=1 ff 00 00 00 00 00 ...
[   11.748011] cfg80211: Calling CRDA to update world regulatory domain
[   11.783896] cfg80211: World regulatory domain updated:
[   11.783903]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   11.783909]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.783916]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.783922]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.783928]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.783933]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.791957] ppdev: user-space parallel port driver
[   11.880016] Linux video capture interface: v2.00
[   11.902371] lirc_dev: IR Remote Control driver registered, major 61 
[   11.905839] 
[   11.905842] lirc_atiusb: USB remote driver for LIRC $Revision: 1.85 $
[   11.905847] lirc_atiusb: Paul Miller <pmiller9@users.sourceforge.net>
[   11.911525] usbcore: registered new interface driver lirc_atiusb
[   11.994973] [drm] radeon defaulting to kernel modesetting.
[   11.994978] [drm] radeon kernel modesetting enabled.
[   11.995067] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.995076] radeon 0000:01:00.0: setting latency timer to 64
[   11.997056] [drm] radeon: Initializing kernel modesetting.
[   12.008751] [drm] register mmio base: 0xD0030000
[   12.008756] [drm] register mmio size: 65536
[   12.011358] ATOM BIOS: MEDION
[   12.011581] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
[   12.011605] [drm] Generation 2 PCI interface, using max accessible memory
[   12.011610] [drm] radeon: VRAM 128M
[   12.011613] [drm] radeon: VRAM from 0x00000000 to 0x07FFFFFF
[   12.011617] [drm] radeon: GTT 512M
[   12.011620] [drm] radeon: GTT from 0x20000000 to 0x3FFFFFFF
[   12.011679]   alloc irq_desc for 26 on node -1
[   12.011684]   alloc kstat_irqs on node -1
[   12.011701] radeon 0000:01:00.0: irq 26 for MSI/MSI-X
[   12.011710] [drm] radeon: using MSI.
[   12.011744] [drm] radeon: irq initialized.
[   12.012445] [drm] Detected VRAM RAM=128M, BAR=128M
[   12.012451] [drm] RAM width 128bits DDR
[   12.028597] [TTM] Zone  kernel: Available graphics memory: 443538 kiB.
[   12.028604] [TTM] Zone highmem: Available graphics memory: 513142 kiB.
[   12.028630] [drm] radeon: 128M of VRAM memory ready
[   12.028635] [drm] radeon: 512M of GTT memory ready.
[   12.028658] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   12.029211] [drm] PCIE GART of 512M enabled (table at 0x00040000).
[   12.029222] [drm] radeon: 2 quad pipes, 1 z pipes initialized.
[   12.029249] [drm] radeon: cp idle (0x10000C03)
[   12.029382] [drm] Loading R400 Microcode
[   12.029776] platform radeon_cp.0: firmware: requesting radeon/R420_cp.bin
[   12.062494] [drm] radeon: ring at 0x0000000020000000
[   12.062518] [drm] ring test succeeded in 1 usecs
[   12.062788] [drm] radeon: ib pool ready.
[   12.062896] [drm] ib test succeeded in 0 usecs
[   12.062945] [drm] Default TV standard: PAL
[   12.063157] [drm] Radeon Display Connectors
[   12.063162] [drm] Connector 0:
[   12.063165] [drm]   VGA
[   12.063170] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   12.063173] [drm]   Encoders:
[   12.063176] [drm]     CRT1: INTERNAL_DAC1
[   12.063180] [drm] Connector 1:
[   12.063182] [drm]   DVI-I
[   12.063185] [drm]   HPD1
[   12.063189] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
[   12.063193] [drm]   Encoders:
[   12.063197] [drm]     DFP1: INTERNAL_TMDS1
[   12.063200] [drm]     CRT2: INTERNAL_DAC2
[   12.081105] saa7130/34: v4l2 driver version 0.2.15 loaded
[   12.081172]   alloc irq_desc for 17 on node -1
[   12.081177]   alloc kstat_irqs on node -1
[   12.081187] saa7134 0000:03:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.081197] saa7134[0]: found at 0000:03:01.0, rev: 1, irq: 17, latency: 32, mmio: 0xd8000000
[   12.081207] saa7134[0]: subsystem: 16be:0003, board: Medion 7134 [card=12,autodetected]
[   12.081229] saa7134[0]: board init: gpio is 0
[   12.081240] IRQ 17/saa7134[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   12.163290] type=1505 audit(1277809890.146:5):  operation="profile_load" pid=741 name="/usr/share/gdm/guest-session/Xsession"
[   12.181705] type=1505 audit(1277809890.166:6):  operation="profile_replace" pid=744 name="/sbin/dhclient3"
[   12.182536] type=1505 audit(1277809890.166:7):  operation="profile_replace" pid=744 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   12.182986] type=1505 audit(1277809890.166::  operation="profile_replace" pid=744 name="/usr/lib/connman/scripts/dhclient-script"
[   12.224840] eth0: link down
[   12.225102] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.232403] type=1505 audit(1277809890.218:9):  operation="profile_load" pid=749 name="/usr/bin/evince"
[   12.258481] type=1505 audit(1277809890.242:10):  operation="profile_load" pid=749 name="/usr/bin/evince-previewer"
[   12.272368] type=1505 audit(1277809890.258:11):  operation="profile_load" pid=749 name="/usr/bin/evince-thumbnailer"
[   12.280033] saa7134[0]: i2c eeprom 00: be 16 03 00 08 20 1c 55 43 43 a9 1c 55 43 43 a9
[   12.280057] saa7134[0]: i2c eeprom 10: ff ff ff ff 15 00 0e 01 0c c0 08 00 00 00 00 00
[   12.280080] saa7134[0]: i2c eeprom 20: 00 00 00 e3 ff ff ff ff ff ff ff ff ff ff ff ff
[   12.280103] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.280125] saa7134[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.280146] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.280167] saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.280189] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.280209] saa7134[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.280229] saa7134[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.280250] saa7134[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.280270] saa7134[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.280291] saa7134[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.280313] saa7134[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.280334] saa7134[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.280360] saa7134[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.280388] i2c i2c-2: Invalid 7-bit address 0x7a
[   12.296064] saa7134[0] Tuner type is 38
[   12.330589] [drm] fb mappable at 0xC80C0000
[   12.330595] [drm] vram apper at 0xC8000000
[   12.330599] [drm] size 3145728
[   12.330602] [drm] fb depth is 24
[   12.330606] [drm]    pitch is 4096
[   12.330821] fb0: radeondrmfb frame buffer device
[   12.330826] registered panic notifier
[   12.330835] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0 on minor 0
[   12.358729] vga16fb: initializing
[   12.358736] vga16fb: mapped to 0xc00a0000
[   12.358743] vga16fb: not registering due to another framebuffer present
[   12.385009] phy0: Selected rate control algorithm 'minstrel'
[   12.386445] Registered led device: rt2500usb-phy0::radio
[   12.386480] Registered led device: rt2500usb-phy0::quality
[   12.387177] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.387224] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   12.387308] usbcore: registered new interface driver rt2500usb
[   12.458207] Console: switching to colour frame buffer device 128x48
[   12.523543] tuner 2-0043: chip found @ 0x86 (saa7134[0])
[   12.594448] tda9887 2-0043: creating new instance
[   12.594453] tda9887 2-0043: tda988[5/6/7] found
[   12.696044] All bytes are equal. It is not a TEA5767
[   12.696244] tuner 2-0060: chip found @ 0xc0 (saa7134[0])
[   12.733494] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   12.744022] Bluetooth: L2CAP ver 2.14
[   12.744027] Bluetooth: L2CAP socket layer initialized
[   12.757753] tuner-simple 2-0060: creating new instance
[   12.757760] tuner-simple 2-0060: type set to 38 (Philips PAL/SECAM multi (FM1216ME MK3))
[   12.759556] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   12.759562] Bluetooth: BNEP filters: protocol multicast
[   12.784267] Bridge firewalling registered
[   12.813738] Bluetooth: SCO (Voice Link) ver 0.6
[   12.813744] Bluetooth: SCO socket layer initialized
[   12.820178] saa7134[0]: registered device video0 [v4l2]
[   12.820247] saa7134[0]: registered device vbi0
[   12.820302] saa7134[0]: registered device radio0
[   12.839307] saa7134 ALSA driver for DMA sound loaded
[   12.839326] IRQ 17/saa7134[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   12.839369] saa7134[0]/alsa: saa7134[0] at 0xd8000000 irq 17 registered as card -2
[   12.942698] dvb_init() allocating 1 frontend
[   12.958642] tda10046: chip is not answering. Giving up.
[   12.958744] saa7134[0]/dvb: frontend initialization failed
[   13.279733] CPU0 attaching NULL sched-domain.
[   13.279761] CPU1 attaching NULL sched-domain.
[   13.296124] CPU0 attaching sched-domain:
[   13.296146]  domain 0: span 0-1 level SIBLING
[   13.296152]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[   13.296164]   domain 1: span 0-1 level MC
[   13.296169]    groups: 0-1 (cpu_power = 117
[   13.296179] CPU1 attaching sched-domain:
[   13.296184]  domain 0: span 0-1 level SIBLING
[   13.296189]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[   13.296201]   domain 1: span 0-1 level MC
[   13.296206]    groups: 0-1 (cpu_power = 117
[   13.344635] Bluetooth: RFCOMM TTY layer initialized
[   13.344642] Bluetooth: RFCOMM socket layer initialized
[   13.344645] Bluetooth: RFCOMM ver 1.11
[   15.131678] CPU0 attaching NULL sched-domain.
[   15.131688] CPU1 attaching NULL sched-domain.
[   15.152126] CPU0 attaching sched-domain:
[   15.152133]  domain 0: span 0-1 level SIBLING
[   15.152139]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[   15.152151]   domain 1: span 0-1 level MC
[   15.152156]    groups: 0-1 (cpu_power = 117
[   15.152166] CPU1 attaching sched-domain:
[   15.152171]  domain 0: span 0-1 level SIBLING
[   15.152176]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[   15.152187]   domain 1: span 0-1 level MC
[   15.152192]    groups: 0-1 (cpu_power = 117
[   16.733951] usb-storage: device scan complete
[   16.735903] scsi 4:0:0:0: Direct-Access     Generic  CF Card       CF 0.1C PQ: 0 ANSI: 0 CCS
[   16.737782] scsi 4:0:0:1: Direct-Access     Generic  MS/SD Combo   MS 0.1C PQ: 0 ANSI: 0 CCS
[   16.739772] scsi 4:0:0:2: Direct-Access     Generic  SM/xD Combo   SM 0.1C PQ: 0 ANSI: 0 CCS
[   16.740992] sd 4:0:0:0: Attached scsi generic sg4 type 0
[   16.741263] sd 4:0:0:1: Attached scsi generic sg5 type 0
[   16.741503] sd 4:0:0:2: Attached scsi generic sg6 type 0
[   16.764324] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[   16.775749] sd 4:0:0:1: [sdd] Attached SCSI removable disk
[   16.776282] sd 4:0:0:2: [sde] Attached SCSI removable disk
[ 1270.800025] usb 1-8: new high speed USB device using ehci_hcd and address 9
[ 1270.935432] usb 1-8: configuration #1 chosen from 1 choice
[ 1270.935815] scsi5 : SCSI emulation for USB Mass Storage devices
[ 1270.935997] usb-storage: device found at 9
[ 1270.936019] usb-storage: waiting for device to settle before scanning
[ 1275.936805] usb-storage: device scan complete
[ 1275.937623] scsi 5:0:0:0: Direct-Access                               0.00 PQ: 0 ANSI: 2
[ 1275.941748] sd 5:0:0:0: Attached scsi generic sg7 type 0
[ 1275.942747] sd 5:0:0:0: [sdf] 15794176 512-byte logical blocks: (8.08 GB/7.53 GiB)
[ 1275.945786] sd 5:0:0:0: [sdf] Write Protect is off
[ 1275.945795] sd 5:0:0:0: [sdf] Mode Sense: 00 00 00 00
[ 1275.945801] sd 5:0:0:0: [sdf] Assuming drive cache: write through
[ 1275.949502] sd 5:0:0:0: [sdf] Assuming drive cache: write through
[ 1275.949513]  sdf:
[ 1276.253909] sd 5:0:0:0: [sdf] Assuming drive cache: write through
[ 1276.253916] sd 5:0:0:0: [sdf] Attached SCSI removable disk
murray@murray-desktop:~$ 

I would be very glad for any and all help or suggestions, thanks. Murox.

---

