---
title: "Integrated Wireless No Connectivity"
date: 2010-03-13
forum: Networking &amp; Wireless
---

### Post by roosh on 2010-03-13
I've been trying to use the wireless adapter that came shipped with my computer for a while now (it is NOT a USB adapter; it seems built into the computer). However, I can't seem to get it working.

HP says that the driver is Lite-On USB Wireless 802.11 b/g Adaptor. The link for Windows download is here: [http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=pv-67706-1&lc=en&dlc=en&cc=us&product=3856266&os=2100]("http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=pv-67706-1&lc=en&dlc=en&cc=us&product=3856266&os=2100")

Note: I am currently connecting to the internet with my netgear USB adapter (I think the driver is something like prism_usb)

Info:

1 ) Machine Brand and Model (PC/Laptop):

It is a desktop, HP A6700f


2 ) Wireless Brand, Model and Wireless Chipset:
Code:

$ lspci
```
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)

```



$ lsusb

I'm not going to post this b/c the wireless adapter I'm trying to get working is NOT connected via USB.


3 ) check interface:
Code:

$ ifconfig

```
eth0      Link encap:Ethernet  HWaddr 00:21:97:4e:f6:7f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:111 errors:0 dropped:0 overruns:0 frame:0
          TX packets:111 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12583 (12.5 KB)  TX bytes:12583 (12.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:5f:6c:2f:3f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan1     Link encap:Ethernet  HWaddr 00:09:5b:91:d9:80  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::209:5bff:fe91:d980/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12127 errors:1 dropped:0 overruns:0 frame:1
          TX packets:10664 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13429464 (13.4 MB)  TX bytes:1333136 (1.3 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-22-5F-6C-2F-3F-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

$ iwconfig

(hint) if the Wireless interface name is wlan0 you can also use
Code:

$ iwconfig wlan0

```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"NETGEAR"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=10 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan1     IEEE 802.11-b  ESSID:"NETGEAR"  Nickname:"NETGEAR"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1E:2A:59:4C:28   
          Bit Rate:11 Mb/s   Tx-Power:18 dBm   
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Link Quality=42/100  Signal level=-73 dBm  Noise level=-91 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

4 ) Check for modules:
Code:

$ lsmod

```
Module                  Size  Used by
prism2_usb            216120  0 
snd_usb_audio         102976  1 
snd_usb_lib            19648  1 snd_usb_audio
usblp                  15136  0 
binfmt_misc            10220  1 
ppdev                   8232  0 
snd_hda_codec_realtek   277860  1 
arc4                    2144  2 
snd_hda_intel          31880  2 
snd_hda_codec          87584  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               9352  2 snd_usb_audio,snd_hda_codec
ecb                     3296  2 
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  4 snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
rt73usb                29092  0 
crc_itu_t               2336  1 rt73usb
rt2x00usb              13600  1 rt73usb
rt2x00lib              34624  2 rt73usb,rt2x00usb
led_class               5256  1 rt2x00lib
input_polldev           4720  1 rt2x00lib
mac80211              210040  2 rt2x00usb,rt2x00lib
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27296  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
amd64_edac_mod         26688  0 
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i2c_nforce2             8168  0 
edac_core              48876  1 amd64_edac_mod
cfg80211              109144  2 rt2x00lib,mac80211
nvidia              10316904  36 
snd                    77096  19 snd_usb_audio,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
psmouse                57124  0 
serio_raw               6596  0 
lp                     11908  0 
parport                40528  2 ppdev,lp
iptable_filter          3872  0 
ip_tables              21200  1 iptable_filter
x_tables               25832  1 ip_tables
dm_raid45              78504  0 
xor                     5456  1 dm_raid45
usb_storage            66304  0 
ohci1394               33780  0 
ieee1394              100896  1 ohci1394
forcedeth              61292  0 

```


5 ) Kernel boot messages
Code:

$ dmesg

```
[    0.710006] Bluetooth: Core ver 2.15

[    0.710021] NET: Registered protocol family 31

[    0.710021] Bluetooth: HCI device and connection manager initialized

[    0.710021] Bluetooth: HCI socket layer initialized

[    0.710021] NetLabel: Initializing

[    0.710021] NetLabel:  domain hash size = 128

[    0.710022] NetLabel:  protocols = UNLABELED CIPSOv4

[    0.710035] NetLabel:  unlabeled traffic allowed by default

[    0.710178] PCI-DMA: Disabling AGP.

[    0.710276] PCI-DMA: aperture base @ 20000000 size 65536 KB

[    0.710277] PCI-DMA: using GART IOMMU.

[    0.710281] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture

[    0.711885] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31

[    0.711893] hpet0: 3 comparators, 32-bit 25.000000 MHz counter

[    0.750017] Switched to high resolution mode on CPU 0

[    0.750708] Switched to high resolution mode on CPU 2

[    0.750714] Switched to high resolution mode on CPU 3

[    0.750817] Switched to high resolution mode on CPU 1

[    0.770030] pnp: PnP ACPI init

[    0.770048] ACPI: bus type pnp registered

[    0.774862] pnp: PnP ACPI: found 12 devices

[    0.774864] ACPI: ACPI bus type pnp unregistered

[    0.774877] system 00:01: ioport range 0x1000-0x107f has been reserved

[    0.774880] system 00:01: ioport range 0x1080-0x10ff has been reserved

[    0.774883] system 00:01: ioport range 0x1400-0x147f has been reserved

[    0.774888] system 00:01: ioport range 0x1480-0x14ff has been reserved

[    0.774891] system 00:01: ioport range 0x1800-0x187f has been reserved

[    0.774894] system 00:01: ioport range 0x1880-0x18ff has been reserved

[    0.774896] system 00:01: ioport range 0x2000-0x207f has been reserved

[    0.774899] system 00:01: ioport range 0x2080-0x20ff has been reserved

[    0.774903] system 00:01: iomem range 0xfec80000-0xfecbffff has been reserved

[    0.774906] system 00:01: iomem range 0xfefe0000-0xfefe01ff has been reserved

[    0.774909] system 00:01: iomem range 0xfefe1000-0xfefe10ff has been reserved

[    0.774915] system 00:01: iomem range 0xb8000000-0xbfffffff has been reserved

[    0.774920] system 00:02: ioport range 0x4d0-0x4d1 has been reserved

[    0.774923] system 00:02: ioport range 0x800-0x87f has been reserved

[    0.774926] system 00:02: ioport range 0x290-0x297 has been reserved

[    0.774933] system 00:0a: iomem range 0xf0000000-0xf3ffffff has been reserved

[    0.774938] system 00:0b: iomem range 0xf0000-0xfffff could not be reserved

[    0.774941] system 00:0b: iomem range 0xfeff0000-0xfeff00ff has been reserved

[    0.774950] system 00:0b: iomem range 0xb7ee0000-0xb7efffff could not be reserved

[    0.774953] system 00:0b: iomem range 0xffff0000-0xffffffff has been reserved

[    0.774956] system 00:0b: iomem range 0x0-0x9ffff could not be reserved

[    0.774959] system 00:0b: iomem range 0x100000-0xb7edffff could not be reserved

[    0.774962] system 00:0b: iomem range 0xb7f00000-0xbfefffff could not be reserved

[    0.774965] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved

[    0.774968] system 00:0b: iomem range 0xfee00000-0xfeefffff has been reserved

[    0.774971] system 00:0b: iomem range 0xfefff000-0xfeffffff has been reserved

[    0.774974] system 00:0b: iomem range 0xfff80000-0xfff80fff has been reserved

[    0.774977] system 00:0b: iomem range 0xfff90000-0xfffbffff has been reserved

[    0.774980] system 00:0b: iomem range 0xfffed000-0xfffeffff has been reserved

[    0.779653] AppArmor: AppArmor Filesystem Enabled

[    0.779686] pci 0000:00:04.0: PCI bridge, secondary bus 0000:01

[    0.779689] pci 0000:00:04.0:   IO window: 0xb000-0xbfff

[    0.779693] pci 0000:00:04.0:   MEM window: 0xfd700000-0xfd7fffff

[    0.779697] pci 0000:00:04.0:   PREFETCH window: 0xfde00000-0xfdefffff

[    0.779702] pci 0000:00:09.0: PCI bridge, secondary bus 0000:02

[    0.779705] pci 0000:00:09.0:   IO window: 0xa000-0xafff

[    0.779708] pci 0000:00:09.0:   MEM window: 0xfdd00000-0xfddfffff

[    0.779711] pci 0000:00:09.0:   PREFETCH window: 0x000000fdc00000-0x000000fdcfffff

[    0.779715] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:03

[    0.779718] pci 0000:00:0b.0:   IO window: 0x9000-0x9fff

[    0.779721] pci 0000:00:0b.0:   MEM window: 0xfdb00000-0xfdbfffff

[    0.779724] pci 0000:00:0b.0:   PREFETCH window: 0x000000fda00000-0x000000fdafffff

[    0.779728] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:04

[    0.779731] pci 0000:00:0c.0:   IO window: 0x8000-0x8fff

[    0.779734] pci 0000:00:0c.0:   MEM window: 0xfd900000-0xfd9fffff

[    0.779737] pci 0000:00:0c.0:   PREFETCH window: 0x000000fd800000-0x000000fd8fffff

[    0.779745] pci 0000:00:04.0: setting latency timer to 64

[    0.779751] pci 0000:00:09.0: setting latency timer to 64

[    0.779756] pci 0000:00:0b.0: setting latency timer to 64

[    0.779760] pci 0000:00:0c.0: setting latency timer to 64

[    0.779764] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]

[    0.779767] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]

[    0.779770] pci_bus 0000:01: resource 0 io:  [0xb000-0xbfff]

[    0.779773] pci_bus 0000:01: resource 1 mem: [0xfd700000-0xfd7fffff]

[    0.779776] pci_bus 0000:01: resource 2 pref mem [0xfde00000-0xfdefffff]

[    0.779778] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]

[    0.779781] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffffffffffff]

[    0.779784] pci_bus 0000:02: resource 0 io:  [0xa000-0xafff]

[    0.779786] pci_bus 0000:02: resource 1 mem: [0xfdd00000-0xfddfffff]

[    0.779789] pci_bus 0000:02: resource 2 pref mem [0xfdc00000-0xfdcfffff]

[    0.779792] pci_bus 0000:03: resource 0 io:  [0x9000-0x9fff]

[    0.779794] pci_bus 0000:03: resource 1 mem: [0xfdb00000-0xfdbfffff]

[    0.779797] pci_bus 0000:03: resource 2 pref mem [0xfda00000-0xfdafffff]

[    0.779800] pci_bus 0000:04: resource 0 io:  [0x8000-0x8fff]

[    0.779802] pci_bus 0000:04: resource 1 mem: [0xfd900000-0xfd9fffff]

[    0.779805] pci_bus 0000:04: resource 2 pref mem [0xfd800000-0xfd8fffff]

[    0.779845] NET: Registered protocol family 2

[    0.780081] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)

[    0.781494] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)

[    0.784921] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)

[    0.785347] TCP: Hash tables configured (established 524288 bind 65536)

[    0.785350] TCP reno registered

[    0.785462] NET: Registered protocol family 1

[    0.785529] Trying to unpack rootfs image as initramfs...

[    0.998997] Freeing initrd memory: 7931k freed

[    1.001261] Clocksource tsc unstable (delta = 341229008 ns)

[    1.002737] Scanning for low memory corruption every 60 seconds

[    1.002868] audit: initializing netlink socket (disabled)

[    1.002884] type=2000 audit(1268472543.000:1): initialized

[    1.012778] HugeTLB registered 2 MB page size, pre-allocated 0 pages

[    1.014500] VFS: Disk quotas dquot_6.5.2

[    1.014560] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)

[    1.015273] fuse init (API version 7.12)

[    1.015363] msgmni has been set to 7671

[    1.015692] alg: No test for stdrng (krng)

[    1.015706] io scheduler noop registered

[    1.015709] io scheduler anticipatory registered

[    1.015711] io scheduler deadline registered

[    1.015756] io scheduler cfq registered (default)

[    1.030113] pci 0000:00:00.0: Found enabled HT MSI Mapping

[    1.030164] pci 0000:00:00.0: Found enabled HT MSI Mapping

[    1.030225] pci 0000:00:00.0: Found enabled HT MSI Mapping

[    1.030284] pci 0000:00:00.0: Found enabled HT MSI Mapping

[    1.030343] pci 0000:00:00.0: Found enabled HT MSI Mapping

[    1.030407] pci 0000:00:00.0: Found enabled HT MSI Mapping

[    1.030476] pci 0000:00:00.0: Found enabled HT MSI Mapping

[    1.030549] pci 0000:00:00.0: Found enabled HT MSI Mapping

[    1.030556] pci 0000:00:0d.0: Boot video device

[    1.030693]   alloc irq_desc for 24 on node 0

[    1.030695]   alloc kstat_irqs on node 0

[    1.030704] pcieport-driver 0000:00:09.0: irq 24 for MSI/MSI-X

[    1.030710] pcieport-driver 0000:00:09.0: setting latency timer to 64

[    1.030827]   alloc irq_desc for 25 on node 0

[    1.030828]   alloc kstat_irqs on node 0

[    1.030833] pcieport-driver 0000:00:0b.0: irq 25 for MSI/MSI-X

[    1.030838] pcieport-driver 0000:00:0b.0: setting latency timer to 64

[    1.030934]   alloc irq_desc for 26 on node 0

[    1.030936]   alloc kstat_irqs on node 0

[    1.030941] pcieport-driver 0000:00:0c.0: irq 26 for MSI/MSI-X

[    1.030945] pcieport-driver 0000:00:0c.0: setting latency timer to 64

[    1.031005] pci_hotplug: PCI Hot Plug PCI Core version: 0.5

[    1.031030] pciehp: PCI Express Hot Plug Controller Driver version: 0.4

[    1.031155] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0

[    1.031159] ACPI: Power Button [PWRF]

[    1.031215] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1

[    1.031218] ACPI: Power Button [PWRB]

[    1.031277] fan PNP0C0B:00: registered as cooling_device0

[    1.031282] ACPI: Fan [FAN] (on)

[    1.031673] processor LNXCPU:00: registered as cooling_device1

[    1.031707] processor LNXCPU:01: registered as cooling_device2

[    1.031743] processor LNXCPU:02: registered as cooling_device3

[    1.031773] processor LNXCPU:03: registered as cooling_device4

[    1.035676] ACPI Warning: \_TZ_.THRM._PSL: Return Package type mismatch at index 0 - found [NULL Object Descriptor], expected Reference 20090521 nspredef-946

[    1.035685] ACPI: Expecting a [Reference] package element, found type 0

[    1.035687] ACPI: Invalid passive threshold

[    1.036006] thermal LNXTHERM:01: registered as thermal_zone0

[    1.036014] ACPI: Thermal Zone [THRM] (40 C)

[    1.037176] Linux agpgart interface v0.103

[    1.037188] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled

[    1.038386] brd: module loaded

[    1.038833] loop: module loaded

[    1.038904] input: Macintosh mouse button emulation as /devices/virtual/input/input2

[    1.039183] sata_nv 0000:00:08.0: version 3.5

[    1.039577] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23

[    1.039581]   alloc irq_desc for 23 on node 0

[    1.039583]   alloc kstat_irqs on node 0

[    1.039594] sata_nv 0000:00:08.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23

[    1.039652] sata_nv 0000:00:08.0: setting latency timer to 64

[    1.039728] scsi0 : sata_nv

[    1.039821] scsi1 : sata_nv

[    1.039999] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 23

[    1.040021] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 23

[    1.040426] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 23

[    1.040430] sata_nv 0000:00:08.1: PCI INT B -> Link[APSJ] -> GSI 23 (level, low) -> IRQ 23

[    1.040460] sata_nv 0000:00:08.1: setting latency timer to 64

[    1.040501] scsi2 : sata_nv

[    1.040561] scsi3 : sata_nv

[    1.040734] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 23

[    1.040737] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 23

[    1.040875] pata_amd 0000:00:06.0: version 0.4.1

[    1.040905] pata_amd 0000:00:06.0: setting latency timer to 64

[    1.040981] scsi4 : pata_amd

[    1.041043] scsi5 : pata_amd

[    1.041658] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14

[    1.041661] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15

[    1.042301] Fixed MDIO Bus: probed

[    1.042333] PPP generic driver version 2.4.2

[    1.042432] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver

[    1.042830] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22

[    1.042835]   alloc irq_desc for 22 on node 0

[    1.042837]   alloc kstat_irqs on node 0

[    1.042847] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 22 (level, low) -> IRQ 22

[    1.042865] ehci_hcd 0000:00:02.1: setting latency timer to 64

[    1.042868] ehci_hcd 0000:00:02.1: EHCI Host Controller

[    1.042911] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1

[    1.042941] ehci_hcd 0000:00:02.1: debug port 1

[    1.042945] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported

[    1.042966] ehci_hcd 0000:00:02.1: irq 22, io mem 0xfe02e000

[    1.060025] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00

[    1.060097] usb usb1: configuration #1 chosen from 1 choice

[    1.060124] hub 1-0:1.0: USB hub found

[    1.060133] hub 1-0:1.0: 10 ports detected

[    1.060224] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver

[    1.060635] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21

[    1.060640]   alloc irq_desc for 21 on node 0

[    1.060642]   alloc kstat_irqs on node 0

[    1.060652] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 21 (level, low) -> IRQ 21

[    1.060668] ohci_hcd 0000:00:02.0: setting latency timer to 64

[    1.060671] ohci_hcd 0000:00:02.0: OHCI Host Controller

[    1.060705] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2

[    1.060732] ohci_hcd 0000:00:02.0: irq 21, io mem 0xfe02f000

[    1.122078] usb usb2: configuration #1 chosen from 1 choice

[    1.122102] hub 2-0:1.0: USB hub found

[    1.122110] hub 2-0:1.0: 10 ports detected

[    1.122173] uhci_hcd: USB Universal Host Controller Interface driver

[    1.122274] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12

[    1.122661] serio: i8042 KBD port at 0x60,0x64 irq 1

[    1.122674] serio: i8042 AUX port at 0x60,0x64 irq 12

[    1.122769] mice: PS/2 mouse device common for all mice

[    1.122864] rtc_cmos 00:05: RTC can wake from S4

[    1.122897] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0

[    1.122934] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs

[    1.123079] device-mapper: uevent: version 1.0.3

[    1.123176] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com

[    1.123331] device-mapper: multipath: version 1.1.0 loaded

[    1.123335] device-mapper: multipath round-robin: version 1.0.0 loaded

[    1.123658] cpuidle: using governor ladder

[    1.123660] cpuidle: using governor menu

[    1.124117] TCP cubic registered

[    1.124265] NET: Registered protocol family 10

[    1.124792] lo: Disabled Privacy Extensions

[    1.125137] NET: Registered protocol family 17

[    1.125157] Bluetooth: L2CAP ver 2.13

[    1.125159] Bluetooth: L2CAP socket layer initialized

[    1.125162] Bluetooth: SCO (Voice Link) ver 0.6

[    1.125164] Bluetooth: SCO socket layer initialized

[    1.125202] Bluetooth: RFCOMM TTY layer initialized

[    1.125205] Bluetooth: RFCOMM socket layer initialized

[    1.125207] Bluetooth: RFCOMM ver 1.11

[    1.125242] powernow-k8: Found 1 AMD Phenom(tm) 9150e Quad-Core Processor processors (4 cpu cores) (version 2.20.00)

[    1.125297] powernow-k8:    0 : pstate 0 (1800 MHz)

[    1.125299] powernow-k8:    1 : pstate 1 (900 MHz)

[    1.125718] PM: Resume from disk failed.

[    1.125731] registered taskstats version 1

[    1.125867]   Magic number: 2:835:474

[    1.125954] rtc_cmos 00:05: setting system clock to 2010-03-13 09:29:03 UTC (1268472543)

[    1.125957] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found

[    1.125959] EDD information not available.

[    1.142811] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3

[    1.380415] ata3: SATA link down (SStatus 0 SControl 300)

[    1.540053] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)

[    1.560162] ata1.00: ATA-8: ST3500620AS, HP24, max UDMA/100

[    1.560165] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)

[    1.600145] ata1.00: configured for UDMA/100

[    1.600246] scsi 0:0:0:0: Direct-Access     ATA      ST3500620AS      HP24 PQ: 0 ANSI: 5

[    1.600371] sd 0:0:0:0: Attached scsi generic sg0 type 0

[    1.600408] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)

[    1.600451] sd 0:0:0:0: [sda] Write Protect is off

[    1.600454] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00

[    1.600477] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

[    1.600594]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 >

[    1.601863] sd 0:0:0:0: [sda] Attached SCSI disk

[    1.740024] usb 1-7: new high speed USB device using ehci_hcd and address 5

[    2.045664] usb 1-7: configuration #1 chosen from 1 choice

[    2.090040] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)

[    2.110132] ata2.00: ATAPI: HL-DT-ST DVD-RAM GH40L, 1.03, max UDMA/100

[    2.150153] ata2.00: configured for UDMA/100

[    2.158708] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GH40L    1.03 PQ: 0 ANSI: 5

[    2.162527] usb 1-9: new high speed USB device using ehci_hcd and address 6

[    2.179693] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray

[    2.179696] Uniform CD-ROM driver Revision: 3.20

[    2.179765] sr 1:0:0:0: Attached scsi CD-ROM sr0

[    2.179808] sr 1:0:0:0: Attached scsi generic sg1 type 5

[    2.314530] usb 1-9: configuration #1 chosen from 1 choice

[    2.510405] ata4: SATA link down (SStatus 0 SControl 300)

[    2.510454] ata6: port disabled. ignoring.

[    2.510480] Freeing unused kernel memory: 664k freed

[    2.510694] Write protecting the kernel read-only data: 7596k

[    2.632342] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.

[    2.632777] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 20

[    2.632784]   alloc irq_desc for 20 on node 0

[    2.632786]   alloc kstat_irqs on node 0

[    2.632798] forcedeth 0000:00:07.0: PCI INT A -> Link[APCH] -> GSI 20 (level, low) -> IRQ 20

[    2.632804] forcedeth 0000:00:07.0: setting latency timer to 64

[    2.654887] usb 2-1: new full speed USB device using ohci_hcd and address 2

[    2.668063] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19

[    2.668070]   alloc irq_desc for 19 on node 0

[    2.668073]   alloc kstat_irqs on node 0

[    2.668085] ohci1394 0000:01:09.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19

[    2.668091] ohci1394 0000:01:09.0: setting latency timer to 64

[    2.679652] Initializing USB Mass Storage driver...

[    2.681189] scsi6 : SCSI emulation for USB Mass Storage devices

[    2.682381] usbcore: registered new interface driver usb-storage

[    2.682386] USB Mass Storage support registered.

[    2.683288] usb-storage: device found at 6

[    2.683292] usb-storage: waiting for device to settle before scanning

[    2.732067] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[fd7ff000-fd7ff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]

[    3.171059] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:21:97:4e:f6:7f

[    3.171065] forcedeth 0000:00:07.0: highdma pwrctl mgmt lnktim msi desc-v3

[    3.610496] xor: automatically using best checksumming function: generic_sse

[    3.660011]    generic_sse:  7394.800 MB/sec

[    3.660014] xor: using function: generic_sse (7394.800 MB/sec)

[    3.662468] device-mapper: dm-raid45: initialized v0.2594b

[    3.867458] PM: Starting manual resume from disk

[    3.867463] PM: Resume from partition 8:5

[    3.867465] PM: Checking hibernation image.

[    3.867757] PM: Resume from disk failed.

[    3.900867] kjournald starting.  Commit interval 5 seconds

[    3.900877] EXT3-fs: mounted filesystem with writeback data mode.

[    4.051486] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00000ae6ffd96b5d]

[    4.423424] type=1505 audit(1268472546.796:2): operation="profile_load" pid=448 name=/usr/share/gdm/guest-session/Xsession

[    4.434627] type=1505 audit(1268472546.806:3): operation="profile_load" pid=449 name=/sbin/dhclient3

[    4.434947] type=1505 audit(1268472546.806:4): operation="profile_load" pid=449 name=/usr/lib/NetworkManager/nm-dhcp-client.action

[    4.435124] type=1505 audit(1268472546.806:5): operation="profile_load" pid=449 name=/usr/lib/connman/scripts/dhclient-script

[    4.454973] type=1505 audit(1268472546.826:6): operation="profile_load" pid=450 name=/usr/bin/evince

[    4.460065] type=1505 audit(1268472546.826:7): operation="profile_load" pid=450 name=/usr/bin/evince-previewer

[    4.463128] type=1505 audit(1268472546.836:8): operation="profile_load" pid=450 name=/usr/bin/evince-thumbnailer

[    4.504083] type=1505 audit(1268472546.876:9): operation="profile_load" pid=452 name=/usr/lib/cups/backend/cups-pdf

[    4.504467] type=1505 audit(1268472546.876:10): operation="profile_load" pid=452 name=/usr/sbin/cupsd

[    7.680185] usb-storage: device scan complete

[    7.680761] scsi 6:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0

[    7.681260] scsi 6:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0

[    7.681754] scsi 6:0:0:2: Direct-Access     Generic  USB xD/SM Reader 1.02 PQ: 0 ANSI: 0

[    7.682252] scsi 6:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0

[    7.682668] sd 6:0:0:0: Attached scsi generic sg2 type 0

[    7.682745] sd 6:0:0:1: Attached scsi generic sg3 type 0

[    7.682816] sd 6:0:0:2: Attached scsi generic sg4 type 0

[    7.682888] sd 6:0:0:3: Attached scsi generic sg5 type 0

[    7.686118] sd 6:0:0:0: [sdb] Attached SCSI removable disk

[    7.686745] sd 6:0:0:1: [sdc] Attached SCSI removable disk

[    7.687367] sd 6:0:0:2: [sdd] Attached SCSI removable disk

[    7.687993] sd 6:0:0:3: [sde] Attached SCSI removable disk

[   14.843962] Adding 10675152k swap on /dev/sda5.  Priority:-1 extents:1 across:10675152k 

[   14.845499] udev: starting version 147

[   15.046924] ip_tables: (C) 2000-2006 Netfilter Core Team

[   15.188668] lp: driver loaded but no devices found

[   15.918646] nvidia: module license 'NVIDIA' taints kernel.

[   15.918651] Disabling lock debugging due to kernel taint

[   15.943370] EDAC MC: Ver: 2.1.0 Feb  8 2010

[   15.945271] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00

[   15.945294] i2c-adapter i2c-1: nForce2 SMBus adapter at 0xf400

[   16.107108] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input4

[   16.174319] ACPI: PCI Interrupt Link [AIGP] enabled at IRQ 22

[   16.174326] nvidia 0000:00:0d.0: PCI INT A -> Link[AIGP] -> GSI 22 (level, low) -> IRQ 22

[   16.174333] nvidia 0000:00:0d.0: setting latency timer to 64

[   16.176030] EDAC amd64_edac:  Ver: 3.2.0 Feb  8 2010

[   16.176081] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  185.18.36  Fri Aug 14 17:35:21 PDT 2009

[   16.177135] EDAC amd64: This node reports that Memory ECC is currently disabled.

[   16.177139] EDAC amd64: bit 0x400000 in register F3x44 of the MISC_CONTROL device (0000:00:18.3) should be enabled

[   16.177142] EDAC amd64: WARNING: ECC is NOT currently enabled by the BIOS. Module will NOT be loaded.

[   16.177144]     Either Enable ECC in the BIOS, or use the 'ecc_enable_override' parameter.

[   16.177145]     Might be a BIOS bug, if BIOS says ECC is enabled

[   16.177146]     Use of the override can cause unknown side effects.

[   16.177163] amd64_edac: probe of 0000:00:18.2 failed with error -22

[   16.330084] cfg80211: Calling CRDA to update world regulatory domain

[   16.354215] cfg80211: World regulatory domain updated:

[   16.354219] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)

[   16.354223] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

[   16.354226] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)

[   16.354229] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)

[   16.354232] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

[   16.354234] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

[   16.363060] EXT3 FS on sda6, internal journal

[   17.075871] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 21

[   17.075878] HDA Intel 0000:00:05.0: PCI INT B -> Link[AAZA] -> GSI 21 (level, low) -> IRQ 21

[   17.075945] HDA Intel 0000:00:05.0: setting latency timer to 64

[   17.446866] phy0: Selected rate control algorithm 'minstrel'

[   17.447563] Registered led device: rt73usb-phy0::radio

[   17.447580] Registered led device: rt73usb-phy0::assoc

[   17.447600] Registered led device: rt73usb-phy0::quality

[   17.448138] usbcore: registered new interface driver rt73usb

[   17.468683] kjournald starting.  Commit interval 5 seconds

[   17.469188] EXT3 FS on sda7, internal journal

[   17.469194] EXT3-fs: mounted filesystem with writeback data mode.

[   17.562155] __ratelimit: 3 callbacks suppressed

[   17.562159] type=1505 audit(1268501359.935:12): operation="profile_replace" pid=1027 name=/usr/share/gdm/guest-session/Xsession

[   17.563983] type=1505 audit(1268501359.935:13): operation="profile_replace" pid=1029 name=/sbin/dhclient3

[   17.564303] type=1505 audit(1268501359.935:14): operation="profile_replace" pid=1029 name=/usr/lib/NetworkManager/nm-dhcp-client.action

[   17.564484] type=1505 audit(1268501359.935:15): operation="profile_replace" pid=1029 name=/usr/lib/connman/scripts/dhclient-script

[   17.568134] type=1505 audit(1268501359.935:16): operation="profile_replace" pid=1031 name=/usr/bin/evince

[   17.573239] type=1505 audit(1268501359.945:17): operation="profile_replace" pid=1031 name=/usr/bin/evince-previewer

[   17.576336] type=1505 audit(1268501359.945:18): operation="profile_replace" pid=1031 name=/usr/bin/evince-thumbnailer

[   17.582457] type=1505 audit(1268501359.955:19): operation="profile_replace" pid=1047 name=/usr/lib/cups/backend/cups-pdf

[   17.582873] type=1505 audit(1268501359.955:20): operation="profile_replace" pid=1047 name=/usr/sbin/cupsd

[   17.585251] type=1505 audit(1268501359.955:21): operation="profile_replace" pid=1050 name=/usr/sbin/tcpdump

[   17.696895] rt73usb 1-7:1.0: firmware: requesting rt73.bin

[   17.838180] ADDRCONF(NETDEV_UP): wlan0: link is not ready

[   17.840238]   alloc irq_desc for 27 on node 0

[   17.840242]   alloc kstat_irqs on node 0

[   17.840253] forcedeth 0000:00:07.0: irq 27 for MSI/MSI-X

[   17.840441] eth0: no link during initialization.

[   17.841297] ADDRCONF(NETDEV_UP): eth0: link is not ready

[   17.842807] usb 2-1: device descriptor read/64, error -110

[   18.560014] hda_codec: Unknown model for ALC1200, trying auto-probe from BIOS...

[   18.600116] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:05.0/input/input5

[   19.146284] ppdev: user-space parallel port driver

[   19.532949] usplash:377 freeing invalid memtype ffffffffe0000000-ffffffffe8000000

[   33.132535] usb 2-1: device descriptor read/64, error -110

[   33.422532] usb 2-1: new full speed USB device using ohci_hcd and address 3

[   48.602522] usb 2-1: device descriptor read/64, error -110

[   63.890021] usb 2-1: device descriptor read/64, error -110

[   64.180018] usb 2-1: new full speed USB device using ohci_hcd and address 4

[   69.213043] usb 2-1: device descriptor read/8, error -110

[   74.340043] usb 2-1: device descriptor read/8, error -110

[   74.630130] usb 2-1: new full speed USB device using ohci_hcd and address 5

[   79.660044] usb 2-1: device descriptor read/8, error -110

[   81.362625] usb 2-1: device descriptor read/8, error -62

[   81.470053] hub 2-0:1.0: unable to enumerate USB device on port 1

[   81.812528] usb 2-3: new full speed USB device using ohci_hcd and address 6

[   82.041192] usb 2-3: configuration #1 chosen from 1 choice

[   82.094133] usblp0: USB Bidirectional printer dev 6 if 0 alt 1 proto 2 vid 0x050D pid 0x0002

[   82.094167] usbcore: registered new interface driver usblp

[   82.380028] usb 2-4: new full speed USB device using ohci_hcd and address 7

[   82.607197] usb 2-4: configuration #1 chosen from 1 choice

[   82.694652] usbcore: registered new interface driver snd-usb-audio

[   83.230039] usb 2-1: new full speed USB device using ohci_hcd and address 8

[   83.448200] usb 2-1: configuration #1 chosen from 1 choice

[   83.522083] prism2_usb: module is from the staging directory, the quality is unknown, you have been warned.

[   83.527026] prism2_usb: Checking for firmware prism2_ru.hex

[   83.527035] usb 2-1: firmware: requesting prism2_ru.hex

[   83.534901] prism2_usb: Firmware not available, but not essential

[   83.534908] prism2_usb: can continue to use card anyway.

[   85.017052] ident: nic h/w: id=0x8026 1.0.0

[   85.019043] ident: pri f/w: id=0x15 1.1.3

[   85.021055] ident: sta f/w: id=0x1f 1.7.0

[   85.023048] MFI:SUP:role=0x00:id=0x01:var=0x01:b/t=1/1

[   85.025044] CFI:SUP:role=0x00:id=0x02:var=0x02:b/t=1/1

[   85.027648] PRI:SUP:role=0x00:id=0x03:var=0x01:b/t=1/4

[   85.029058] STA:SUP:role=0x00:id=0x04:var=0x01:b/t=1/12

[   85.031044] PRI-CFI:ACT:role=0x01:id=0x02:var=0x02:b/t=1/1

[   85.033156] STA-CFI:ACT:role=0x01:id=0x02:var=0x02:b/t=1/1

[   85.035369] STA-MFI:ACT:role=0x01:id=0x01:var=0x01:b/t=1/1

[   85.037575] Prism2 card SN: \x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00

[   85.046518] usbcore: registered new interface driver prism2_usb

[   85.050287] usb 2-3: usbfs: interface 0 claimed by usblp while 'usb' sets config #1

[   85.579050] linkstatus=DISCONNECTED (unhandled)

[   85.583012] ADDRCONF(NETDEV_UP): wlan1: link is not ready

[   96.203071] linkstatus=CONNECTED

[   96.215127] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready

[  106.290065] wlan1: no IPv6 routers present

[  259.601616] usb 2-3: usbfs: interface 0 claimed by usblp while 'usb' sets config #1

[  558.581057] CTLX[3] error: state(Request failed)

[  558.581065] error fetching commsqual

[ 1719.942880] hda-intel: Too big adjustment 32

[ 1720.048191] hda-intel: Too big adjustment 32

```

Note: Line [17.696895] seems to be of importance and so does line [17.447563] and the ones after it.

6 ) Network configuration
Code:

$ sudo lshw -C network

```
  *-network:0             
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:22:5f:6c:2f:3f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan1
       serial: 00:09:5b:91:d9:80
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.4 multicast=yes wireless=IEEE 802.11-b

```

7 ) Scan for networks:
Code:

$ iwlist scan

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

wlan1     No scan results
```

8 ) Ubuntu Version:
Code:

$ lsb_release -d

```
Description:	Ubuntu 9.10

```

9 ) Kernel/architecture (including 32 vs. 64 bit):
Code:

$ uname -mr

```
2.6.31-20-generic x86_64

```

10 ) Restarting the network:
Code:

$ sudo /etc/init.d/networking restart
```
 * Reconfiguring network interfaces...                                          Ignoring unknown interface wlan1=wlan1.
                                                                         [ OK ]
```


Please help, I've tried unsuccessfully to connect for almost a year now.

---

### Post by mikewhatever on 2010-03-13
First, thanks for all the info posted. I think the device you mentioned, Lite-On 802.11 b/g is a usb device connected internally, so you might be able to see it listed under lsusb. Having googled for a bit, I found reports of it using ralink drivers under windows, and accidentally, you seem to have ralink modules loaded (rt73usb, etc). Not quite sure these are the right ones for the device.

---

### Post by roosh on 2010-03-13
lsusb:

```
Bus 002 Device 008: ID 0846:4110 NetGear, Inc. MA111(v1) 802.11b Wireless [Intersil Prism 3.0]
Bus 002 Device 007: ID 0d8c:0103 C-Media Electronics, Inc. Turtle Beach Audio Advantage Micro
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 18e3:9102 Fitipower Integrated Technology Inc Multi car reader
Bus 001 Device 005: ID 15a9:0004  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Note: the netgear works fine (its not the adapter I'm having trouble with).


I did mess around a bit trying to find a way to get the wireless to work, because it did not initially work well with 9.10 (it very very very rarely got Internet). However, I am pretty sure that the rt73 driver is correct...

---

### Post by roosh on 2010-06-11
Any help? By the way, I made a clean install of 10.04, but the problem still persists...

---

