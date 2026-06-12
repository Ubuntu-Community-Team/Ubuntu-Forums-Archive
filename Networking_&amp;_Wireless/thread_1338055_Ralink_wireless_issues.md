---
title: "Ralink wireless issues"
date: 2009-11-26
forum: Networking &amp; Wireless
---

### Post by roosh on 2009-11-26
I've been having trouble connecting to the internet with the ralink wireless that shipped with my computer. Some info:

1 ) Machine Brand and Model (PC/Laptop):

```
Desktop - HP A6700f originally with vista home premium

```

2 ) Wireless Brand, Model and Wireless Chipset:
Code:

$ lspci:
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


$ lsusb:

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
roosh@roosh-desktop:~$ lsusb
Bus 001 Device 005: ID 18e3:9102 Fitipower Integrated Technology Inc Multi car reader
Bus 001 Device 004: ID 15a9:0004  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 004: ID 0846:4110 NetGear, Inc. MA111(v1) 802.11b Wireless [Intersil Prism 3.0]
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```


3 ) check interface:
Code:

$ ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:21:97:4e:f6:7f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:84 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9251 (9.2 KB)  TX bytes:9251 (9.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:5f:6c:2f:3f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan1     Link encap:Ethernet  HWaddr 00:09:5b:91:d9:80  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::209:5bff:fe91:d980/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2053 errors:1 dropped:0 overruns:0 frame:1
          TX packets:2105 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1557066 (1.5 MB)  TX bytes:343902 (343.9 KB)
```




$ iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  Mode:Managed  Access Point: Not-Associated   
          Tx-Power=13 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
wlan1     IEEE 802.11-b  ESSID:"NETGEAR"  Nickname:"NETGEAR"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1E:2A:59:4C:28   
          Bit Rate:11 Mb/s   Tx-Power:18 dBm   
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Link Quality=30/100  Signal level=-78 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```


4 ) Check for modules:
Code:

$ lsmod:

```
Module                  Size  Used by
prism2_usb            216120  0 
binfmt_misc            10220  1 
ppdev                   8232  0 
snd_hda_codec_realtek   277860  1 
arc4                    2144  2 
ecb                     3296  2 
rt73usb                28548  0 
snd_hda_intel          31880  2 
snd_hda_codec          87584  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
crc_itu_t               2336  1 rt73usb
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
rt2x00usb              13600  1 rt73usb
rt2x00lib              34464  2 rt73usb,rt2x00usb
led_class               5256  1 rt2x00lib
mac80211              243360  2 rt2x00usb,rt2x00lib
cfg80211              152424  2 rt2x00lib,mac80211
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27360  1 snd_seq_midi
amd64_edac_mod         26688  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
edac_core              48876  1 amd64_edac_mod
nvidia              10316904  36 
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i2c_nforce2             8168  0 
snd                    77096  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
psmouse                57124  0 
serio_raw               6596  0 
sbp2                   27180  0 
usblp                  15136  0 
iptable_filter          3872  0 
ip_tables              21200  1 iptable_filter
x_tables               25832  1 ip_tables
lp                     11908  0 
parport                40528  2 ppdev,lp
usb_storage            65952  0 
ohci1394               33780  0 
forcedeth              61292  0 
ieee1394              100896  2 sbp2,ohci1394
```

5 ) Kernel boot messages
Code:

$ dmesg:
```

[    0.680400] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[    0.680607] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
[    0.680810] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[    0.681020] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[    0.681230] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[    0.681436] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[    0.681643] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22) *0
[    0.681849] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0
[    0.682056] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0
[    0.682264] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22) *0
[    0.682471] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22) *0
[    0.682678] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22) *0
[    0.682885] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0
[    0.683091] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
[    0.683299] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
[    0.683508] ACPI: PCI Interrupt Link [APSI] (IRQs 23) *0
[    0.683709] ACPI: PCI Interrupt Link [APSJ] (IRQs 23) *0
[    0.683897] SCSI subsystem initialized
[    0.683937] libata version 3.00 loaded.
[    0.683937] usbcore: registered new interface driver usbfs
[    0.683937] usbcore: registered new interface driver hub
[    0.683937] usbcore: registered new device driver usb
[    0.683937] ACPI: WMI: Mapper loaded
[    0.683937] PCI: Using ACPI for IRQ routing
[    0.710006] Bluetooth: Core ver 2.15
[    0.710021] NET: Registered protocol family 31
[    0.710021] Bluetooth: HCI device and connection manager initialized
[    0.710021] Bluetooth: HCI socket layer initialized
[    0.710021] NetLabel: Initializing
[    0.710021] NetLabel:  domain hash size = 128
[    0.710021] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.710035] NetLabel:  unlabeled traffic allowed by default
[    0.710177] PCI-DMA: Disabling AGP.
[    0.710272] PCI-DMA: aperture base @ 20000000 size 65536 KB
[    0.710274] PCI-DMA: using GART IOMMU.
[    0.710277] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.711884] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[    0.711892] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.750016] Switched to high resolution mode on CPU 0
[    0.750697] Switched to high resolution mode on CPU 2
[    0.750703] Switched to high resolution mode on CPU 3
[    0.750721] Switched to high resolution mode on CPU 1
[    0.770030] pnp: PnP ACPI init
[    0.770049] ACPI: bus type pnp registered
[    0.774849] pnp: PnP ACPI: found 12 devices
[    0.774852] ACPI: ACPI bus type pnp unregistered
[    0.774864] system 00:01: ioport range 0x1000-0x107f has been reserved
[    0.774867] system 00:01: ioport range 0x1080-0x10ff has been reserved
[    0.774870] system 00:01: ioport range 0x1400-0x147f has been reserved
[    0.774873] system 00:01: ioport range 0x1480-0x14ff has been reserved
[    0.774879] system 00:01: ioport range 0x1800-0x187f has been reserved
[    0.774884] system 00:01: ioport range 0x1880-0x18ff has been reserved
[    0.774887] system 00:01: ioport range 0x2000-0x207f has been reserved
[    0.774890] system 00:01: ioport range 0x2080-0x20ff has been reserved
[    0.774900] system 00:01: iomem range 0xfec80000-0xfecbffff has been reserved
[    0.774903] system 00:01: iomem range 0xfefe0000-0xfefe01ff has been reserved
[    0.774906] system 00:01: iomem range 0xfefe1000-0xfefe10ff has been reserved
[    0.774909] system 00:01: iomem range 0xb8000000-0xbfffffff has been reserved
[    0.774920] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.774923] system 00:02: ioport range 0x800-0x87f has been reserved
[    0.774925] system 00:02: ioport range 0x290-0x297 has been reserved
[    0.774932] system 00:0a: iomem range 0xf0000000-0xf3ffffff has been reserved
[    0.774937] system 00:0b: iomem range 0xf0000-0xfffff could not be reserved
[    0.774941] system 00:0b: iomem range 0xfeff0000-0xfeff00ff has been reserved
[    0.774949] system 00:0b: iomem range 0xb7ee0000-0xb7efffff could not be reserved
[    0.774952] system 00:0b: iomem range 0xffff0000-0xffffffff has been reserved
[    0.774955] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    0.774958] system 00:0b: iomem range 0x100000-0xb7edffff could not be reserved
[    0.774961] system 00:0b: iomem range 0xb7f00000-0xbfefffff could not be reserved
[    0.774964] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.774967] system 00:0b: iomem range 0xfee00000-0xfeefffff has been reserved
[    0.774970] system 00:0b: iomem range 0xfefff000-0xfeffffff has been reserved
[    0.774973] system 00:0b: iomem range 0xfff80000-0xfff80fff has been reserved
[    0.774976] system 00:0b: iomem range 0xfff90000-0xfffbffff has been reserved
[    0.774979] system 00:0b: iomem range 0xfffed000-0xfffeffff has been reserved
[    0.779658] AppArmor: AppArmor Filesystem Enabled
[    0.779696] pci 0000:00:04.0: PCI bridge, secondary bus 0000:01
[    0.779699] pci 0000:00:04.0:   IO window: 0xb000-0xbfff
[    0.779703] pci 0000:00:04.0:   MEM window: 0xfd700000-0xfd7fffff
[    0.779707] pci 0000:00:04.0:   PREFETCH window: 0xfde00000-0xfdefffff
[    0.779711] pci 0000:00:09.0: PCI bridge, secondary bus 0000:02
[    0.779714] pci 0000:00:09.0:   IO window: 0xa000-0xafff
[    0.779717] pci 0000:00:09.0:   MEM window: 0xfdd00000-0xfddfffff
[    0.779721] pci 0000:00:09.0:   PREFETCH window: 0x000000fdc00000-0x000000fdcfffff
[    0.779725] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:03
[    0.779727] pci 0000:00:0b.0:   IO window: 0x9000-0x9fff
[    0.779730] pci 0000:00:0b.0:   MEM window: 0xfdb00000-0xfdbfffff
[    0.779734] pci 0000:00:0b.0:   PREFETCH window: 0x000000fda00000-0x000000fdafffff
[    0.779737] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:04
[    0.779740] pci 0000:00:0c.0:   IO window: 0x8000-0x8fff
[    0.779743] pci 0000:00:0c.0:   MEM window: 0xfd900000-0xfd9fffff
[    0.779746] pci 0000:00:0c.0:   PREFETCH window: 0x000000fd800000-0x000000fd8fffff
[    0.779755] pci 0000:00:04.0: setting latency timer to 64
[    0.779760] pci 0000:00:09.0: setting latency timer to 64
[    0.779764] pci 0000:00:0b.0: setting latency timer to 64
[    0.779769] pci 0000:00:0c.0: setting latency timer to 64
[    0.779773] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.779776] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.779779] pci_bus 0000:01: resource 0 io:  [0xb000-0xbfff]
[    0.779782] pci_bus 0000:01: resource 1 mem: [0xfd700000-0xfd7fffff]
[    0.779784] pci_bus 0000:01: resource 2 pref mem [0xfde00000-0xfdefffff]
[    0.779787] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
[    0.779789] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.779792] pci_bus 0000:02: resource 0 io:  [0xa000-0xafff]
[    0.779795] pci_bus 0000:02: resource 1 mem: [0xfdd00000-0xfddfffff]
[    0.779797] pci_bus 0000:02: resource 2 pref mem [0xfdc00000-0xfdcfffff]
[    0.779800] pci_bus 0000:03: resource 0 io:  [0x9000-0x9fff]
[    0.779803] pci_bus 0000:03: resource 1 mem: [0xfdb00000-0xfdbfffff]
[    0.779805] pci_bus 0000:03: resource 2 pref mem [0xfda00000-0xfdafffff]
[    0.779808] pci_bus 0000:04: resource 0 io:  [0x8000-0x8fff]
[    0.779810] pci_bus 0000:04: resource 1 mem: [0xfd900000-0xfd9fffff]
[    0.779813] pci_bus 0000:04: resource 2 pref mem [0xfd800000-0xfd8fffff]
[    0.779850] NET: Registered protocol family 2
[    0.780092] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.781498] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.784931] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.785358] TCP: Hash tables configured (established 524288 bind 65536)
[    0.785361] TCP reno registered
[    0.785473] NET: Registered protocol family 1
[    0.785543] Trying to unpack rootfs image as initramfs...
[    0.991282] Freeing initrd memory: 7692k freed
[    0.994891] Scanning for low memory corruption every 60 seconds
[    0.995027] audit: initializing netlink socket (disabled)
[    0.995042] type=2000 audit(1259191875.990:1): initialized
[    1.001259] Clocksource tsc unstable (delta = 341132975 ns)
[    1.004983] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.006716] VFS: Disk quotas dquot_6.5.2
[    1.006775] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.007520] fuse init (API version 7.12)
[    1.007614] msgmni has been set to 7671
[    1.007946] alg: No test for stdrng (krng)
[    1.007961] io scheduler noop registered
[    1.007964] io scheduler anticipatory registered
[    1.007966] io scheduler deadline registered
[    1.008015] io scheduler cfq registered (default)
[    1.021056] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    1.021107] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    1.021168] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    1.021228] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    1.021292] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    1.021357] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    1.021427] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    1.021501] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    1.021507] pci 0000:00:0d.0: Boot video device
[    1.021645]   alloc irq_desc for 24 on node 0
[    1.021647]   alloc kstat_irqs on node 0
[    1.021656] pcieport-driver 0000:00:09.0: irq 24 for MSI/MSI-X
[    1.021662] pcieport-driver 0000:00:09.0: setting latency timer to 64
[    1.021779]   alloc irq_desc for 25 on node 0
[    1.021781]   alloc kstat_irqs on node 0
[    1.021785] pcieport-driver 0000:00:0b.0: irq 25 for MSI/MSI-X
[    1.021790] pcieport-driver 0000:00:0b.0: setting latency timer to 64
[    1.021887]   alloc irq_desc for 26 on node 0
[    1.021889]   alloc kstat_irqs on node 0
[    1.021893] pcieport-driver 0000:00:0c.0: irq 26 for MSI/MSI-X
[    1.021898] pcieport-driver 0000:00:0c.0: setting latency timer to 64
[    1.021958] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.021983] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.022105] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.022109] ACPI: Power Button [PWRF]
[    1.022165] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.022168] ACPI: Power Button [PWRB]
[    1.022233] fan PNP0C0B:00: registered as cooling_device0
[    1.022238] ACPI: Fan [FAN] (on)
[    1.022616] processor LNXCPU:00: registered as cooling_device1
[    1.022646] processor LNXCPU:01: registered as cooling_device2
[    1.022679] processor LNXCPU:02: registered as cooling_device3
[    1.022713] processor LNXCPU:03: registered as cooling_device4
[    1.026619] ACPI Warning: \_TZ_.THRM._PSL: Return Package type mismatch at index 0 - found [NULL Object Descriptor], expected Reference 20090521 nspredef-946
[    1.026628] ACPI: Expecting a [Reference] package element, found type 0
[    1.026631] ACPI: Invalid passive threshold
[    1.026951] thermal LNXTHERM:01: registered as thermal_zone0
[    1.026959] ACPI: Thermal Zone [THRM] (40 C)
[    1.028150] Linux agpgart interface v0.103
[    1.028160] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.029374] brd: module loaded
[    1.029829] loop: module loaded
[    1.029899] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.030240] sata_nv 0000:00:08.0: version 3.5
[    1.030632] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[    1.030637]   alloc irq_desc for 23 on node 0
[    1.030640]   alloc kstat_irqs on node 0
[    1.030650] sata_nv 0000:00:08.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    1.030710] sata_nv 0000:00:08.0: setting latency timer to 64
[    1.030783] scsi0 : sata_nv
[    1.030872] scsi1 : sata_nv
[    1.031042] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 23
[    1.031046] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 23
[    1.031445] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 23
[    1.031449] sata_nv 0000:00:08.1: PCI INT B -> Link[APSJ] -> GSI 23 (level, low) -> IRQ 23
[    1.031476] sata_nv 0000:00:08.1: setting latency timer to 64
[    1.031524] scsi2 : sata_nv
[    1.031582] scsi3 : sata_nv
[    1.031743] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 23
[    1.031750] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 23
[    1.031879] pata_amd 0000:00:06.0: version 0.4.1
[    1.031905] pata_amd 0000:00:06.0: setting latency timer to 64
[    1.031979] scsi4 : pata_amd
[    1.032040] scsi5 : pata_amd
[    1.032638] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    1.032641] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    1.033260] Fixed MDIO Bus: probed
[    1.033293] PPP generic driver version 2.4.2
[    1.033391] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.033760] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[    1.033765]   alloc irq_desc for 22 on node 0
[    1.033767]   alloc kstat_irqs on node 0
[    1.033777] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 22 (level, low) -> IRQ 22
[    1.033794] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    1.033798] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    1.033856] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    1.033886] ehci_hcd 0000:00:02.1: debug port 1
[    1.033890] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    1.033911] ehci_hcd 0000:00:02.1: irq 22, io mem 0xfe02e000
[    1.042225] ata3: SATA link down (SStatus 0 SControl 300)
[    1.050042] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    1.050111] usb usb1: configuration #1 chosen from 1 choice
[    1.050139] hub 1-0:1.0: USB hub found
[    1.050148] hub 1-0:1.0: 10 ports detected
[    1.050232] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.050749] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
[    1.050753]   alloc irq_desc for 21 on node 0
[    1.050755]   alloc kstat_irqs on node 0
[    1.050764] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 21 (level, low) -> IRQ 21
[    1.050779] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    1.050782] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    1.050818] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    1.050845] ohci_hcd 0000:00:02.0: irq 21, io mem 0xfe02f000
[    1.112088] usb usb2: configuration #1 chosen from 1 choice
[    1.112113] hub 2-0:1.0: USB hub found
[    1.112121] hub 2-0:1.0: 10 ports detected
[    1.112192] uhci_hcd: USB Universal Host Controller Interface driver
[    1.112297] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.112691] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.112704] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.112797] mice: PS/2 mouse device common for all mice
[    1.112893] rtc_cmos 00:05: RTC can wake from S4
[    1.112929] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.112967] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    1.113093] device-mapper: uevent: version 1.0.3
[    1.113186] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.113336] device-mapper: multipath: version 1.1.0 loaded
[    1.113340] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.113666] cpuidle: using governor ladder
[    1.113669] cpuidle: using governor menu
[    1.114141] TCP cubic registered
[    1.114297] NET: Registered protocol family 10
[    1.114803] lo: Disabled Privacy Extensions
[    1.115160] NET: Registered protocol family 17
[    1.115179] Bluetooth: L2CAP ver 2.13
[    1.115181] Bluetooth: L2CAP socket layer initialized
[    1.115184] Bluetooth: SCO (Voice Link) ver 0.6
[    1.115186] Bluetooth: SCO socket layer initialized
[    1.115225] Bluetooth: RFCOMM TTY layer initialized
[    1.115228] Bluetooth: RFCOMM socket layer initialized
[    1.115230] Bluetooth: RFCOMM ver 1.11
[    1.115267] powernow-k8: Found 1 AMD Phenom(tm) 9150e Quad-Core Processor processors (4 cpu cores) (version 2.20.00)
[    1.115310] powernow-k8:    0 : pstate 0 (1800 MHz)
[    1.115312] powernow-k8:    1 : pstate 1 (900 MHz)
[    1.115718] PM: Resume from disk failed.
[    1.115730] registered taskstats version 1
[    1.115877]   Magic number: 1:828:555
[    1.115909] pci_link PNP0C0F:06: hash matches
[    1.115967] rtc_cmos 00:05: setting system clock to 2009-11-25 23:31:17 UTC (1259191877)
[    1.115971] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.115972] EDD information not available.
[    1.133609] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.191299] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.211398] ata1.00: ATA-8: ST3500620AS, HP24, max UDMA/100
[    1.211402] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.250160] ata1.00: configured for UDMA/100
[    1.250265] scsi 0:0:0:0: Direct-Access     ATA      ST3500620AS      HP24 PQ: 0 ANSI: 5
[    1.250394] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.250434] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.250469] sd 0:0:0:0: [sda] Write Protect is off
[    1.250472] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.250493] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.250611]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    1.284790] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.410046] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.430155] ata2.00: ATAPI: HL-DT-ST DVD-RAM GH40L, 1.03, max UDMA/100
[    1.470150] ata2.00: configured for UDMA/100
[    1.478707] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GH40L    1.03 PQ: 0 ANSI: 5
[    1.499694] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.499697] Uniform CD-ROM driver Revision: 3.20
[    1.499759] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.499802] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.510228] ata4: SATA link down (SStatus 0 SControl 300)
[    1.510276] ata6: port disabled. ignoring.
[    1.510306] Freeing unused kernel memory: 660k freed
[    1.510522] Write protecting the kernel read-only data: 7580k
[    1.621274] usb 1-7: new high speed USB device using ehci_hcd and address 4
[    1.661770] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.662175] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 20
[    1.662181]   alloc irq_desc for 20 on node 0
[    1.662183]   alloc kstat_irqs on node 0
[    1.662195] forcedeth 0000:00:07.0: PCI INT A -> Link[APCH] -> GSI 20 (level, low) -> IRQ 20
[    1.662200] forcedeth 0000:00:07.0: setting latency timer to 64
[    1.664793] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[    1.664796]   alloc irq_desc for 19 on node 0
[    1.664798]   alloc kstat_irqs on node 0
[    1.664806] ohci1394 0000:01:09.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
[    1.664811] ohci1394 0000:01:09.0: setting latency timer to 64
[    1.732083] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[fd7ff000-fd7ff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    1.929394] usb 1-7: configuration #1 chosen from 1 choice
[    2.043782] usb 1-9: new high speed USB device using ehci_hcd and address 5
[    2.195640] usb 1-9: configuration #1 chosen from 1 choice
[    2.201067] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:21:97:4e:f6:7f
[    2.201072] forcedeth 0000:00:07.0: highdma pwrctl mgmt lnktim msi desc-v3
[    2.203097] Initializing USB Mass Storage driver...
[    2.203438] scsi6 : SCSI emulation for USB Mass Storage devices
[    2.203536] usb-storage: device found at 5
[    2.203540] usb-storage: waiting for device to settle before scanning
[    2.203545] usbcore: registered new interface driver usb-storage
[    2.203549] USB Mass Storage support registered.
[    2.551277] usb 2-1: new full speed USB device using ohci_hcd and address 2
[    2.748851] PM: Starting manual resume from disk
[    2.748857] PM: Resume from partition 8:6
[    2.748859] PM: Checking hibernation image.
[    2.749150] PM: Resume from disk failed.
[    2.774931] kjournald starting.  Commit interval 5 seconds
[    2.774941] EXT3-fs: mounted filesystem with writeback data mode.
[    3.063967] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00000ae6ffd96b5d]
[    3.557397] type=1505 audit(1259191879.934:2): operation="profile_load" pid=421 name=/usr/share/gdm/guest-session/Xsession
[    3.575791] type=1505 audit(1259191879.957:3): operation="profile_load" pid=422 name=/sbin/dhclient3
[    3.576109] type=1505 audit(1259191879.957:4): operation="profile_load" pid=422 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    3.576289] type=1505 audit(1259191879.957:5): operation="profile_load" pid=422 name=/usr/lib/connman/scripts/dhclient-script
[    3.621190] type=1505 audit(1259191879.997:6): operation="profile_load" pid=423 name=/usr/bin/evince
[    3.626137] type=1505 audit(1259191880.007:7): operation="profile_load" pid=423 name=/usr/bin/evince-previewer
[    3.629064] type=1505 audit(1259191880.007:8): operation="profile_load" pid=423 name=/usr/bin/evince-thumbnailer
[    3.651431] type=1505 audit(1259191880.027:9): operation="profile_load" pid=425 name=/usr/lib/cups/backend/cups-pdf
[    3.651821] type=1505 audit(1259191880.027:10): operation="profile_load" pid=425 name=/usr/sbin/cupsd
[    4.836674] Adding 10675152k swap on /dev/sda6.  Priority:-1 extents:1 across:10675152k 
[    7.200250] usb-storage: device scan complete
[    7.200842] scsi 6:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[    7.201349] scsi 6:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[    7.201858] scsi 6:0:0:2: Direct-Access     Generic  USB xD/SM Reader 1.02 PQ: 0 ANSI: 0
[    7.202323] scsi 6:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[    7.202687] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    7.202764] sd 6:0:0:1: Attached scsi generic sg3 type 0
[    7.202839] sd 6:0:0:2: Attached scsi generic sg4 type 0
[    7.202912] sd 6:0:0:3: Attached scsi generic sg5 type 0
[    7.206447] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    7.207324] sd 6:0:0:1: [sdc] Attached SCSI removable disk
[    7.208072] sd 6:0:0:2: [sdd] Attached SCSI removable disk
[    7.208796] sd 6:0:0:3: [sde] Attached SCSI removable disk
[   16.213849] hub 2-0:1.0: unable to enumerate USB device on port 1
[   16.553836] usb 2-3: new full speed USB device using ohci_hcd and address 3
[   16.781135] usb 2-3: configuration #1 chosen from 1 choice
[   21.521689] udev: starting version 147
[   23.223440] lp: driver loaded but no devices found
[   23.306499] ip_tables: (C) 2000-2006 Netfilter Core Team
[   23.523852] usblp0: USB Bidirectional printer dev 3 if 0 alt 1 proto 2 vid 0x050D pid 0x0002
[   23.523873] usbcore: registered new interface driver usblp
[   23.930980] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   23.931005] i2c-adapter i2c-1: nForce2 SMBus adapter at 0xf400
[   24.363501] nvidia: module license 'NVIDIA' taints kernel.
[   24.363507] Disabling lock debugging due to kernel taint
[   24.374031] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[   24.619961] ACPI: PCI Interrupt Link [AIGP] enabled at IRQ 22
[   24.619969] nvidia 0000:00:0d.0: PCI INT A -> Link[AIGP] -> GSI 22 (level, low) -> IRQ 22
[   24.619976] nvidia 0000:00:0d.0: setting latency timer to 64
[   24.620268] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  185.18.36  Fri Aug 14 17:35:21 PDT 2009
[   24.739670] EDAC MC: Ver: 2.1.0 Oct 16 2009
[   24.752718] EDAC amd64_edac:  Ver: 3.2.0 Oct 16 2009
[   24.752824] EDAC amd64: This node reports that Memory ECC is currently disabled.
[   24.752832] EDAC amd64: bit 0x400000 in register F3x44 of the MISC_CONTROL device (0000:00:18.3) should be enabled
[   24.752835] EDAC amd64: WARNING: ECC is NOT currently enabled by the BIOS. Module will NOT be loaded.
[   24.752836]     Either Enable ECC in the BIOS, or use the 'ecc_enable_override' parameter.
[   24.752838]     Might be a BIOS bug, if BIOS says ECC is enabled
[   24.752839]     Use of the override can cause unknown side effects.
[   24.752858] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   25.983835] cfg80211: Calling CRDA to update world regulatory domain
[   26.611030] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 21
[   26.611038] HDA Intel 0000:00:05.0: PCI INT B -> Link[AAZA] -> GSI 21 (level, low) -> IRQ 21
[   26.611094] HDA Intel 0000:00:05.0: setting latency timer to 64
[   26.645726] cfg80211: World regulatory domain updated:
[   26.645731] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   26.645735] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.645738] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   26.645741] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   26.645743] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.645745] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   27.311357] phy0: Selected rate control algorithm 'minstrel'
[   27.312137] Registered led device: rt73usb-phy0::radio
[   27.312155] Registered led device: rt73usb-phy0::assoc
[   27.312174] Registered led device: rt73usb-phy0::quality
[   27.312711] usbcore: registered new interface driver rt73usb
[   28.080026] hda_codec: Unknown model for ALC1200, trying auto-probe from BIOS...
[   28.120089] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:05.0/input/input5
[  247.199309] EXT3 FS on sda5, internal journal
[  248.474404] __ratelimit: 3 callbacks suppressed
[  248.474408] type=1505 audit(1259220924.857:12): operation="profile_replace" pid=1059 name=/usr/share/gdm/guest-session/Xsession
[  248.543693] type=1505 audit(1259220924.917:13): operation="profile_replace" pid=1066 name=/sbin/dhclient3
[  248.544014] type=1505 audit(1259220924.927:14): operation="profile_replace" pid=1066 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[  248.544191] type=1505 audit(1259220924.927:15): operation="profile_replace" pid=1066 name=/usr/lib/connman/scripts/dhclient-script
[  248.640478] usplash:361 freeing invalid memtype ffffffffe0000000-ffffffffe8000000
[  248.705691] type=1505 audit(1259220925.087:16): operation="profile_replace" pid=1067 name=/usr/bin/evince
[  248.711093] type=1505 audit(1259220925.087:17): operation="profile_replace" pid=1067 name=/usr/bin/evince-previewer
[  248.714237] type=1505 audit(1259220925.097:18): operation="profile_replace" pid=1067 name=/usr/bin/evince-thumbnailer
[  248.778294] type=1505 audit(1259220925.157:19): operation="profile_replace" pid=1075 name=/usr/lib/cups/backend/cups-pdf
[  248.778687] type=1505 audit(1259220925.157:20): operation="profile_replace" pid=1075 name=/usr/sbin/cupsd
[  248.854609] type=1505 audit(1259220925.237:21): operation="profile_replace" pid=1088 name=/usr/sbin/tcpdump
[  248.995504] rt73usb 1-7:1.0: firmware: requesting rt73.bin
[  249.115644] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  249.117628]   alloc irq_desc for 27 on node 0
[  249.117633]   alloc kstat_irqs on node 0
[  249.117644] forcedeth 0000:00:07.0: irq 27 for MSI/MSI-X
[  249.117833] eth0: no link during initialization.
[  249.118712] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  253.198913] ppdev: user-space parallel port driver
[  254.379958] usb 2-3: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[  267.940019] usb 2-1: new full speed USB device using ohci_hcd and address 4
[  268.157137] usb 2-1: configuration #1 chosen from 1 choice
[  268.232907] prism2_usb: module is from the staging directory, the quality is unknown, you have been warned.
[  268.235426] prism2_usb: Checking for firmware prism2_ru.hex
[  268.235431] usb 2-1: firmware: requesting prism2_ru.hex
[  268.239452] prism2_usb: Firmware not available, but not essential
[  268.239456] prism2_usb: can continue to use card anyway.
[  269.694048] ident: nic h/w: id=0x8026 1.0.0
[  269.696038] ident: pri f/w: id=0x15 1.1.3
[  269.698039] ident: sta f/w: id=0x1f 1.7.0
[  269.700039] MFI:SUP:role=0x00:id=0x01:var=0x01:b/t=1/1
[  269.702038] CFI:SUP:role=0x00:id=0x02:var=0x02:b/t=1/1
[  269.704045] PRI:SUP:role=0x00:id=0x03:var=0x01:b/t=1/4
[  269.706040] STA:SUP:role=0x00:id=0x04:var=0x01:b/t=1/12
[  269.708038] PRI-CFI:ACT:role=0x01:id=0x02:var=0x02:b/t=1/1
[  269.710039] STA-CFI:ACT:role=0x01:id=0x02:var=0x02:b/t=1/1
[  269.712038] STA-MFI:ACT:role=0x01:id=0x01:var=0x01:b/t=1/1
[  269.714046] Prism2 card SN: \x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00
[  269.722777] usbcore: registered new interface driver prism2_usb
[  270.148043] linkstatus=DISCONNECTED (unhandled)
[  270.151106] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  281.331060] linkstatus=CONNECTED
[  281.342624] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  291.843764] wlan1: no IPv6 routers present
[  369.533810] CTLX[3] error: state(Request failed)
[  369.533818] error fetching commsqual
```



6 ) Network configuration
Code:

$ sudo lshw -C network:

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
       configuration: broadcast=yes ip=192.168.1.3 multicast=yes wireless=IEEE 802.11-b
```




7 ) Scan for networks:
Code:

$ iwlist scan:

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

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
2.6.31-14-generic x86_64
```


10 ) Restarting the network:
Code:

$ sudo /etc/init.d/networking restart

```
 * Reconfiguring network interfaces...                                                                       Ignoring unknown interface wlan1=wlan1.
                                                                                                      [ OK ]
```


Additional info: I'm pretty sure that the wlan0 is the ralink. Wlan1 is the current (and very old) wireless USB adapter I use, but I want to get the other one to work. I also am pretty sure that the ralink uses a rt73 driver. I've had this problem for awhile (in both Ubuntu 8.10 and 9.04).  Very rarely the ralink does connect to the internet, but at very, very slow speeds compared to how it runs in vista.

Thanks for any help!

---

