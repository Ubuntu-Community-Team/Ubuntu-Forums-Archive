---
title: "Wifi Link 5050 Series Problems"
date: 2010-01-21
forum: Networking &amp; Wireless
---

### Post by j_p36 on 2010-01-21
To preface this, I don't have much Linux experience.

I have a Lenovo Y550 Laptop with problems connecting to wifi when using ubuntu

Network controller: Intel Corporation WiMAX/WiFi Link 5050 Series

Ubuntu 9.10

2.6.31-17-generic x86_64

The network manager detects the WiMax side of the card but doesn't detect the Wifi side. wlan0 isn't even an option in the network areas.

I've tried the linux drivers provided from intel (can't really figure that out) and ndiswrapper also.  I have tried multiple versions of windows drivers and the device always ends up UNCLAIMED.  Currently I have installed through ndiswrapper, the windows 7 driver for intel wifi 5150

```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:22:0c:53:7f  
          inet addr:130.18.206.97  Bcast:130.18.206.255  Mask:255.255.255.0
          inet6 addr: fe80::226:22ff:fe0c:537f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:579 errors:0 dropped:0 overruns:0 frame:0
          TX packets:433 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:584906 (584.9 KB)  TX bytes:64720 (64.7 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```
lsmod
Module                  Size  Used by
binfmt_misc            10220  1 
ppdev                   8232  0 
bridge                 56384  0 
stp                     3012  1 bridge
bnep                   15168  2 
snd_hda_codec_realtek   277860  1 
snd_hda_codec_nvhdmi     6048  1 
uvcvideo               65260  0 
videodev               43360  1 uvcvideo
v4l1_compat            16804  2 uvcvideo,videodev
v4l2_compat_ioctl32    13344  1 videodev
iptable_filter          3872  0 
btusb                  14260  2 
joydev                 13088  0 
snd_hda_intel          31880  2 
snd_hda_codec          87584  3 snd_hda_codec_realtek,snd_hda_codec_nvhdmi,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ip_tables              21200  1 iptable_filter
x_tables               25832  1 ip_tables
ndiswrapper           245280  0 
nvidia              10316904  29 
psmouse                57124  0 
serio_raw               6596  0 
snd                    77096  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
lp                     11908  0 
parport                40528  2 ppdev,lp
usbhid                 43968  0 
tg3                   123748  0 
intel_agp              32816  0 
video                  23612  0 
output                  3680  1 video
```Not really sure what I would be looking for in the dmesg output, otherthan the ndiswrapper stuff
```

dmesg

[    0.436882] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.436979] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.437061] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.437116] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.437177] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.437232] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    0.437287] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.445167] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    0.445260] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.445352] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 *3 4 5 6 7 10 12 14 15)
[    0.445443] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.445534] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    0.445625] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.445716] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.445806] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 *4 5 6 7 11 12 14 15)
[    0.445948] SCSI subsystem initialized
[    0.446221] libata version 3.00 loaded.
[    0.446221] usbcore: registered new interface driver usbfs
[    0.446221] usbcore: registered new interface driver hub
[    0.446221] usbcore: registered new device driver usb
[    0.446221] ACPI: WMI: Mapper loaded
[    0.446221] PCI: Using ACPI for IRQ routing
[    0.470005] Bluetooth: Core ver 2.15
[    0.470016] NET: Registered protocol family 31
[    0.470016] Bluetooth: HCI device and connection manager initialized
[    0.470016] NetLabel: Initializing
[    0.470016] NetLabel:  domain hash size = 128
[    0.470016] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.470026] NetLabel:  unlabeled traffic allowed by default
[    0.470065] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.470070] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.501393] Switched to high resolution mode on CPU 1
[    0.509999] Switched to high resolution mode on CPU 0
[    0.510008] pnp: PnP ACPI init
[    0.510015] ACPI: bus type pnp registered
[    0.530733] pnp: PnP ACPI: found 11 devices
[    0.530735] ACPI: ACPI bus type pnp unregistered
[    0.530744] system 00:04: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.530749] system 00:06: ioport range 0x680-0x69f has been reserved
[    0.530751] system 00:06: ioport range 0x480-0x48f has been reserved
[    0.530753] system 00:06: ioport range 0xffff-0xffff has been reserved
[    0.530756] system 00:06: ioport range 0xffff-0xffff has been reserved
[    0.530758] system 00:06: ioport range 0x400-0x47f has been reserved
[    0.530760] system 00:06: ioport range 0x1180-0x11ff has been reserved
[    0.530762] system 00:06: ioport range 0x164e-0x164f has been reserved
[    0.530764] system 00:06: ioport range 0xfe00-0xfe00 has been reserved
[    0.530769] system 00:0a: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.530771] system 00:0a: iomem range 0xfed10000-0xfed13fff has been reserved
[    0.530774] system 00:0a: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.530776] system 00:0a: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.530778] system 00:0a: iomem range 0xe0000000-0xefffffff has been reserved
[    0.530780] system 00:0a: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.530782] system 00:0a: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.535427] AppArmor: AppArmor Filesystem Enabled
[    0.535512] pci 0000:01:00.0: BAR 6: can't allocate mem resource [0xe0000000-0xdfffffff]
[    0.535515] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.535517] pci 0000:00:01.0:   IO window: 0x2000-0x2fff
[    0.535520] pci 0000:00:01.0:   MEM window: 0xf4000000-0xf6ffffff
[    0.535523] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.535527] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.535528] pci 0000:00:1c.0:   IO window: disabled
[    0.535534] pci 0000:00:1c.0:   MEM window: disabled
[    0.535537] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.535542] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.535543] pci 0000:00:1c.1:   IO window: disabled
[    0.535548] pci 0000:00:1c.1:   MEM window: disabled
[    0.535552] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.535556] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:04
[    0.535557] pci 0000:00:1c.2:   IO window: disabled
[    0.535563] pci 0000:00:1c.2:   MEM window: 0xf7100000-0xf71fffff
[    0.535567] pci 0000:00:1c.2:   PREFETCH window: disabled
[    0.535571] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:05
[    0.535574] pci 0000:00:1c.3:   IO window: 0x3000-0x3fff
[    0.535579] pci 0000:00:1c.3:   MEM window: 0xf0000000-0xf3ffffff
[    0.535584] pci 0000:00:1c.3:   PREFETCH window: 0x000000f8000000-0x000000f9ffffff
[    0.535591] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:07
[    0.535592] pci 0000:00:1c.4:   IO window: disabled
[    0.535597] pci 0000:00:1c.4:   MEM window: disabled
[    0.535601] pci 0000:00:1c.4:   PREFETCH window: disabled
[    0.535606] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:08
[    0.535607] pci 0000:00:1c.5:   IO window: disabled
[    0.535612] pci 0000:00:1c.5:   MEM window: 0xf7000000-0xf70fffff
[    0.535616] pci 0000:00:1c.5:   PREFETCH window: disabled
[    0.535620] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:09
[    0.535622] pci 0000:00:1e.0:   IO window: disabled
[    0.535627] pci 0000:00:1e.0:   MEM window: disabled
[    0.535631] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.535640]   alloc irq_desc for 16 on node 0
[    0.535641]   alloc kstat_irqs on node 0
[    0.535645] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.535648] pci 0000:00:01.0: setting latency timer to 64
[    0.535655]   alloc irq_desc for 17 on node 0
[    0.535656]   alloc kstat_irqs on node 0
[    0.535659] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.535663] pci 0000:00:1c.0: setting latency timer to 64
[    0.535671] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.535675] pci 0000:00:1c.1: setting latency timer to 64
[    0.535682]   alloc irq_desc for 18 on node 0
[    0.535683]   alloc kstat_irqs on node 0
[    0.535686] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.535690] pci 0000:00:1c.2: setting latency timer to 64
[    0.535697]   alloc irq_desc for 19 on node 0
[    0.535698]   alloc kstat_irqs on node 0
[    0.535701] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.535705] pci 0000:00:1c.3: setting latency timer to 64
[    0.535713] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.535717] pci 0000:00:1c.4: setting latency timer to 64
[    0.535724] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.535729] pci 0000:00:1c.5: setting latency timer to 64
[    0.535736] pci 0000:00:1e.0: setting latency timer to 64
[    0.535740] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.535741] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.535743] pci_bus 0000:01: resource 0 io:  [0x2000-0x2fff]
[    0.535745] pci_bus 0000:01: resource 1 mem: [0xf4000000-0xf6ffffff]
[    0.535747] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.535749] pci_bus 0000:04: resource 1 mem: [0xf7100000-0xf71fffff]
[    0.535751] pci_bus 0000:05: resource 0 io:  [0x3000-0x3fff]
[    0.535753] pci_bus 0000:05: resource 1 mem: [0xf0000000-0xf3ffffff]
[    0.535755] pci_bus 0000:05: resource 2 pref mem [0xf8000000-0xf9ffffff]
[    0.535757] pci_bus 0000:08: resource 1 mem: [0xf7000000-0xf70fffff]
[    0.535759] pci_bus 0000:09: resource 3 io:  [0x00-0xffff]
[    0.535760] pci_bus 0000:09: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.535785] NET: Registered protocol family 2
[    0.535920] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.536906] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.540507] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.540971] TCP: Hash tables configured (established 524288 bind 65536)
[    0.540973] TCP reno registered
[    0.541069] NET: Registered protocol family 1
[    0.541126] Trying to unpack rootfs image as initramfs...
[    0.686690] Freeing initrd memory: 7693k freed
[    0.689464] Simple Boot Flag at 0x36 set to 0x1
[    0.689628] Scanning for low memory corruption every 60 seconds
[    0.689751] audit: initializing netlink socket (disabled)
[    0.689766] type=2000 audit(1264078102.680:1): initialized
[    0.697736] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.698876] VFS: Disk quotas dquot_6.5.2
[    0.698920] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.699361] fuse init (API version 7.12)
[    0.699428] msgmni has been set to 7919
[    0.699589] alg: No test for stdrng (krng)
[    0.699599] io scheduler noop registered
[    0.699601] io scheduler anticipatory registered
[    0.699603] io scheduler deadline registered
[    0.699636] io scheduler cfq registered (default)
[    0.699821] pci 0000:01:00.0: Boot video device
[    0.699936]   alloc irq_desc for 24 on node 0
[    0.699938]   alloc kstat_irqs on node 0
[    0.699945] pcieport-driver 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.699950] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    0.700083]   alloc irq_desc for 25 on node 0
[    0.700084]   alloc kstat_irqs on node 0
[    0.700092] pcieport-driver 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.700102] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.700253]   alloc irq_desc for 26 on node 0
[    0.700254]   alloc kstat_irqs on node 0
[    0.700262] pcieport-driver 0000:00:1c.1: irq 26 for MSI/MSI-X
[    0.700271] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    0.700421]   alloc irq_desc for 27 on node 0
[    0.700422]   alloc kstat_irqs on node 0
[    0.700430] pcieport-driver 0000:00:1c.2: irq 27 for MSI/MSI-X
[    0.700440] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    0.700594]   alloc irq_desc for 28 on node 0
[    0.700596]   alloc kstat_irqs on node 0
[    0.700603] pcieport-driver 0000:00:1c.3: irq 28 for MSI/MSI-X
[    0.700613] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    0.700764]   alloc irq_desc for 29 on node 0
[    0.700766]   alloc kstat_irqs on node 0
[    0.700773] pcieport-driver 0000:00:1c.4: irq 29 for MSI/MSI-X
[    0.700783] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    0.700932]   alloc irq_desc for 30 on node 0
[    0.700934]   alloc kstat_irqs on node 0
[    0.700942] pcieport-driver 0000:00:1c.5: irq 30 for MSI/MSI-X
[    0.700951] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    0.701050] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.701231] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.709163] ACPI: AC Adapter [ACAD] (on-line)
[    0.709219] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.709222] ACPI: Power Button [PWRF]
[    0.709264] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.709308] ACPI: Lid Switch [LID0]
[    0.709340] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    0.709342] ACPI: Power Button [PWRB]
[    0.709376] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3
[    0.709377] ACPI: Sleep Button [SLPB]
[    0.710157] ACPI: SSDT 00000000bfd1ac20 00265 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.710582] ACPI: SSDT 00000000bfd18620 00549 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.712566] Monitor-Mwait will be used to enter C-1 state
[    0.712583] Monitor-Mwait will be used to enter C-2 state
[    0.712589] Marking TSC unstable due to TSC halts in idle
[    0.712599] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    0.712617] processor LNXCPU:00: registered as cooling_device0
[    0.712620] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.716593] ACPI: SSDT 00000000bfd19ca0 001CF (v01  PmRef    ApIst 00003000 INTL 20050624)
[    0.716918] ACPI: SSDT 00000000bfd19f20 0008D (v01  PmRef    ApCst 00003000 INTL 20050624)
[    0.721863] ACPI: CPU1 (power states: C1[C1] C2[C2])
[    0.721876] processor LNXCPU:01: registered as cooling_device1
[    0.721879] ACPI: Processor [CPU1] (supports 8 throttling states)
[    0.750050] ACPI: Invalid active0 threshold
[    0.758899] thermal LNXTHERM:01: registered as thermal_zone0
[    0.758905] ACPI: Thermal Zone [TZ00] (53 C)
[    0.759915] Linux agpgart interface v0.103
[    0.759921] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.760874] brd: module loaded
[    0.761213] loop: module loaded
[    0.761266] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.761349] ahci 0000:00:1f.2: version 3.0
[    0.761361] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.761394]   alloc irq_desc for 31 on node 0
[    0.761396]   alloc kstat_irqs on node 0
[    0.761404] ahci 0000:00:1f.2: irq 31 for MSI/MSI-X
[    0.761438] ahci: SSS flag set, parallel bus scan disabled
[    0.761468] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x13 impl SATA mode
[    0.761471] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ems 
[    0.761476] ahci 0000:00:1f.2: setting latency timer to 64
[    0.800051] scsi0 : ahci
[    0.800122] scsi1 : ahci
[    0.800164] scsi2 : ahci
[    0.800210] scsi3 : ahci
[    0.800254] scsi4 : ahci
[    0.800285] ata1: SATA max UDMA/133 abar m2048@0xf7405000 port 0xf7405100 irq 31
[    0.800288] ata2: SATA max UDMA/133 abar m2048@0xf7405000 port 0xf7405180 irq 31
[    0.800290] ata3: DUMMY
[    0.800291] ata4: DUMMY
[    0.800293] ata5: SATA max UDMA/133 abar m2048@0xf7405000 port 0xf7405300 irq 31
[    0.800940] Fixed MDIO Bus: probed
[    0.800965] PPP generic driver version 2.4.2
[    0.801029] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.801071]   alloc irq_desc for 20 on node 0
[    0.801073]   alloc kstat_irqs on node 0
[    0.801077] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 20 (level, low) -> IRQ 20
[    0.801087] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.801090] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.801127] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.805037] ehci_hcd 0000:00:1a.7: debug port 1
[    0.805042] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.805053] ehci_hcd 0000:00:1a.7: irq 20, io mem 0xf7405800
[    0.820012] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.820076] usb usb1: configuration #1 chosen from 1 choice
[    0.820098] hub 1-0:1.0: USB hub found
[    0.820103] hub 1-0:1.0: 6 ports detected
[    0.820182]   alloc irq_desc for 23 on node 0
[    0.820184]   alloc kstat_irqs on node 0
[    0.820187] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.820195] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.820198] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.820223] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.824140] ehci_hcd 0000:00:1d.7: debug port 1
[    0.824146] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.824156] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf7405c00
[    0.840012] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.840061] usb usb2: configuration #1 chosen from 1 choice
[    0.840080] hub 2-0:1.0: USB hub found
[    0.840085] hub 2-0:1.0: 6 ports detected
[    0.840137] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.840151] uhci_hcd: USB Universal Host Controller Interface driver
[    0.840211] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.840217] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.840220] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.840246] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.840276] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001800
[    0.840340] usb usb3: configuration #1 chosen from 1 choice
[    0.840359] hub 3-0:1.0: USB hub found
[    0.840364] hub 3-0:1.0: 2 ports detected
[    0.840426]   alloc irq_desc for 21 on node 0
[    0.840427]   alloc kstat_irqs on node 0
[    0.840430] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.840436] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.840438] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.840463] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.840493] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001820
[    0.840551] usb usb4: configuration #1 chosen from 1 choice
[    0.840572] hub 4-0:1.0: USB hub found
[    0.840576] hub 4-0:1.0: 2 ports detected
[    0.840635] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 20 (level, low) -> IRQ 20
[    0.840640] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.840643] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.840669] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.840694] uhci_hcd 0000:00:1a.2: irq 20, io base 0x00001840
[    0.840755] usb usb5: configuration #1 chosen from 1 choice
[    0.840774] hub 5-0:1.0: USB hub found
[    0.840778] hub 5-0:1.0: 2 ports detected
[    0.840846] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.840851] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.840854] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.840879] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.840902] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001860
[    0.840962] usb usb6: configuration #1 chosen from 1 choice
[    0.840981] hub 6-0:1.0: USB hub found
[    0.840987] hub 6-0:1.0: 2 ports detected
[    0.841049] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.841054] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.841057] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.841079] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.841109] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001880
[    0.841169] usb usb7: configuration #1 chosen from 1 choice
[    0.841188] hub 7-0:1.0: USB hub found
[    0.841193] hub 7-0:1.0: 2 ports detected
[    0.841253] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.841259] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.841262] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.841289] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.841319] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
[    0.841377] usb usb8: configuration #1 chosen from 1 choice
[    0.841398] hub 8-0:1.0: USB hub found
[    0.841406] hub 8-0:1.0: 2 ports detected
[    0.841482] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:MSS1] at 0x60,0x64 irq 1,12
[    0.895874] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.895879] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.895921] mice: PS/2 mouse device common for all mice
[    0.896020] rtc_cmos 00:07: RTC can wake from S4
[    0.896049] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    0.896077] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.896170] device-mapper: uevent: version 1.0.3
[    0.898574] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.898636] device-mapper: multipath: version 1.1.0 loaded
[    0.898639] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.898927] cpuidle: using governor ladder
[    0.898994] cpuidle: using governor menu
[    0.899299] TCP cubic registered
[    0.899394] NET: Registered protocol family 10
[    0.899722] lo: Disabled Privacy Extensions
[    0.899943] NET: Registered protocol family 17
[    0.899957] Bluetooth: L2CAP ver 2.13
[    0.899958] Bluetooth: L2CAP socket layer initialized
[    0.899961] Bluetooth: SCO (Voice Link) ver 0.6
[    0.899963] Bluetooth: SCO socket layer initialized
[    0.899986] Bluetooth: RFCOMM TTY layer initialized
[    0.899991] Bluetooth: RFCOMM socket layer initialized
[    0.899992] Bluetooth: RFCOMM ver 1.11
[    0.904725] PM: Resume from disk failed.
[    0.904735] registered taskstats version 1
[    0.904835]   Magic number: 10:605:835
[    0.904936] rtc_cmos 00:07: setting system clock to 2010-01-21 12:48:23 UTC (1264078103)
[    0.904939] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.904940] EDD information not available.
[    0.945391] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    0.995884] ACPI: Battery Slot [BAT1] (battery present)
[    1.000534] Clocksource tsc unstable (delta = -74768109 ns)
[    1.152554] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.154484] ata1.00: ATA-8: WDC WD5000BEVT-22ZAT0, 01.01A01, max UDMA/133
[    1.154488] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.156516] ata1.00: configured for UDMA/133
[    1.170221] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000BEVT-2 01.0 PQ: 0 ANSI: 5
[    1.170335] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.170363] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.170397] sd 0:0:0:0: [sda] Write Protect is off
[    1.170399] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.170417] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.170513]  sda: sda1 sda2 < sda5 sda6 > sda3
[    1.220823] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.260123] usb 1-3: new high speed USB device using ehci_hcd and address 3
[    1.413331] usb 1-3: configuration #1 chosen from 1 choice
[    1.590062] usb 2-3: new high speed USB device using ehci_hcd and address 2
[    1.920054] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.921889] ata2.00: ATAPI: Optiarc BD ROM BC-5500S, B802, max UDMA/100
[    1.923837] ata2.00: configured for UDMA/100
[    1.941052] scsi 1:0:0:0: CD-ROM            Optiarc  BD ROM BC-5500S  B802 PQ: 0 ANSI: 5
[    1.943699] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.943702] Uniform CD-ROM driver Revision: 3.20
[    1.943788] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.943834] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.292555] ata5: SATA link down (SStatus 0 SControl 300)
[    2.312554] Freeing unused kernel memory: 660k freed
[    2.312748] Write protecting the kernel read-only data: 7584k
[    2.440840] acpi device:04: registered as cooling_device2
[    2.441033] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/device:02/input/input6
[    2.441069] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    2.475277] tg3.c:v3.99 (April 20, 2009)
[    2.475299] tg3 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.475311] tg3 0000:08:00.0: setting latency timer to 64
[    2.490540] tg3 0000:08:00.0: PME# disabled
[    2.899502] usb 2-3: configuration #1 chosen from 1 choice
[    3.180102] usb 3-1: new full speed USB device using uhci_hcd and address 2
[    3.361482] usb 3-1: configuration #1 chosen from 1 choice
[    3.650101] usb 5-2: new low speed USB device using uhci_hcd and address 2
[    3.831397] eth0: Tigon3 [partno(BCM95784M) rev 5784100] (PCI Express) MAC address 00:26:22:0c:53:7f
[    3.831400] eth0: attached PHY is 5784 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    3.831402] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    3.831403] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    3.834922] usb 5-2: configuration #1 chosen from 1 choice
[    3.841591] usbcore: registered new interface driver hiddev
[    3.864220] input: Primax Lenovo 2.4G Wireless Travel Laser Mouse  as /devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/input/input7
[    3.864303] generic-usb 0003:17EF:6006.0001: input,hiddev96,hidraw0: USB HID v1.11 Mouse [Primax Lenovo 2.4G Wireless Travel Laser Mouse ] on usb-0000:00:1a.2-2/input0
[    3.864313] usbcore: registered new interface driver usbhid
[    3.864315] usbhid: v2.6:USB HID core driver
[    5.110055] kjournald starting.  Commit interval 5 seconds
[    5.110063] EXT3-fs: mounted filesystem with writeback data mode.
[    5.846966] type=1505 audit(1264078108.435:2): operation="profile_load" pid=439 name=/usr/share/gdm/guest-session/Xsession
[    5.857579] type=1505 audit(1264078108.445:3): operation="profile_load" pid=440 name=/sbin/dhclient3
[    5.858214] type=1505 audit(1264078108.445:4): operation="profile_load" pid=440 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    5.858504] type=1505 audit(1264078108.445:5): operation="profile_load" pid=440 name=/usr/lib/connman/scripts/dhclient-script
[    5.891582] type=1505 audit(1264078108.485:6): operation="profile_load" pid=441 name=/usr/bin/evince
[    5.900179] type=1505 audit(1264078108.495:7): operation="profile_load" pid=441 name=/usr/bin/evince-previewer
[    5.905232] type=1505 audit(1264078108.495:8): operation="profile_load" pid=441 name=/usr/bin/evince-thumbnailer
[    5.934847] type=1505 audit(1264078108.525:9): operation="profile_load" pid=443 name=/usr/lib/cups/backend/cups-pdf
[    5.935581] type=1505 audit(1264078108.525:10): operation="profile_load" pid=443 name=/usr/sbin/cupsd
[    5.953788] type=1505 audit(1264078108.545:11): operation="profile_load" pid=444 name=/usr/sbin/tcpdump
[   24.745199] udev: starting version 147
[   24.752487] lp: driver loaded but no devices found
[   24.812246] EXT3 FS on sda6, internal journal
[   24.940739] nvidia: module license 'NVIDIA' taints kernel.
[   24.940742] Disabling lock debugging due to kernel taint
[   24.947785] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   24.956202] ip_tables: (C) 2000-2006 Netfilter Core Team
[   25.126438] Bluetooth: Generic Bluetooth USB driver ver 0.5
[   25.126533] usbcore: registered new interface driver btusb
[   25.205216] Linux video capture interface: v2.00
[   25.207344] uvcvideo: Found UVC 1.00 device Lenovo EasyCamera (090c:7371)
[   25.211310] input: Lenovo EasyCamera as /devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3:1.0/input/input8
[   25.211357] usbcore: registered new interface driver uvcvideo
[   25.211360] USB Video Class driver (v0.1.0)
[   25.214593] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   25.214616] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   25.214636] nvidia 0000:01:00.0: setting latency timer to 64
[   25.214825] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  185.18.36  Fri Aug 14 17:35:21 PDT 2009
[   25.257772] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   25.257782]   alloc irq_desc for 22 on node 0
[   25.257783]   alloc kstat_irqs on node 0
[   25.257788] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   25.257822] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   25.429324] type=1505 audit(1264099728.015:12): operation="profile_replace" pid=972 name=/usr/share/gdm/guest-session/Xsession
[   25.430555] type=1505 audit(1264099728.025:13): operation="profile_replace" pid=973 name=/sbin/dhclient3
[   25.431086] type=1505 audit(1264099728.025:14): operation="profile_replace" pid=973 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   25.431377] type=1505 audit(1264099728.025:15): operation="profile_replace" pid=973 name=/usr/lib/connman/scripts/dhclient-script
[   25.433815] type=1505 audit(1264099728.025:16): operation="profile_replace" pid=974 name=/usr/bin/evince
[   25.446114] type=1505 audit(1264099728.035:17): operation="profile_replace" pid=974 name=/usr/bin/evince-previewer
[   25.451553] type=1505 audit(1264099728.045:18): operation="profile_replace" pid=974 name=/usr/bin/evince-thumbnailer
[   25.452416] hda_codec: Unknown model for ALC272, trying auto-probe from BIOS...
[   25.453285] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input9
[   25.495779] type=1505 audit(1264099728.085:19): operation="profile_replace" pid=1017 name=/usr/lib/cups/backend/cups-pdf
[   25.496434] type=1505 audit(1264099728.085:20): operation="profile_replace" pid=1017 name=/usr/sbin/cupsd
[   25.498256] type=1505 audit(1264099728.085:21): operation="profile_replace" pid=1018 name=/usr/sbin/tcpdump
[   25.511853] tg3 0000:08:00.0: PME# disabled
[   25.512168]   alloc irq_desc for 32 on node 0
[   25.512171]   alloc kstat_irqs on node 0
[   25.512187] tg3 0000:08:00.0: irq 32 for MSI/MSI-X
[   25.662753] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.720097] usb 1-3: reset high speed USB device using ehci_hcd and address 3
[   26.133470] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'RtlUpcaseUnicodeChar'
[   26.133485] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'RtlUnicodeToMultiByteN'
[   26.133489] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'RtlAnsiCharToUnicodeChar'
[   26.133496] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[   26.133500] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[   26.133502] ndiswrapper (load_sys_files:206): couldn't prepare driver 'bpusb'
[   26.142558] ndiswrapper (load_wrap_driver:108): couldn't load driver bpusb; check system log for messages from 'loadndisdriver'
[   26.157675] usbcore: registered new interface driver ndiswrapper
[   26.219241] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04731/0xa40000
[   26.276329] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   26.276332] Bluetooth: BNEP filters: protocol multicast
[   26.281370] Bridge firewalling registered
[   26.338080] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input10
[   26.412499] ppdev: user-space parallel port driver
[   26.985061] usplash:382 freeing invalid memtype fffffffff5000000-fffffffff5e00000
[   58.140007] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x212f000c
[  204.361084] tg3: eth0: Link is up at 100 Mbps, full duplex.
[  204.361092] tg3: eth0: Flow control is off for TX and off for RX.
[  204.362177] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  214.660066] eth0: no IPv6 routers present
``````
lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: WiMAX/WiFi Link 5050 Series
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f7100000-f7101fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 00:26:22:0c:53:7f
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=sb v2.19 ip=130.18.206.97 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:32 memory:f7000000-f700ffff
``````
iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.
``````
sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                Ignoring unknown interface eth0=eth0.
WARNING: ifup -a is disabled in favour of NetworkManager.
  Set ifupdown:managed=false in /etc/NetworkManager/nm-system-settings.conf.
                                                                               [ OK ]
```

---

### Post by adam814 on 2010-01-21
I'm not sure if the "iwlagn" driver supports your device.  It handles most of the other 5000 series cards, so it might be worth a shot.  Try loading the module and post the output of dmesg afterwards.

P.S. I noticed you also don't have the ndiswrapper module loaded either.  You'll have to load either iwlagn or ndiswrapper to have a chance at getting it to work.  I also believe ndiswrapper only supports (or at very least strongly prefers) XP drivers and they have to match your architecture (64-bit XP driver for 64-bit Ubuntu).

So for good measure try one or the other of these:
```
sudo modprobe iwlagn
``````
sudo modprobe ndiswrapper
```

---

### Post by preserve on 2010-01-21
I just installed a Linksys wmp54gs and was having problems very similar to yours. The WARNING after a networking restart was the same as you listed. Wpa_supplicant showed "accepted" but no IP was taken from the wireless router. I finally tried sudo /etc/init.d/wpa-ifupdown start and then stop rather than spawn the wpa_supplicant as a daemon as I had been doing. At that point the wireless connected immediately in NetworkManager.

Take a look at this URL:

[http://blog.avirtualhome.com/2008/03/10/ubuntu-shutdown-problem-cifs-related/](http://blog.avirtualhome.com/2008/03/10/ubuntu-shutdown-problem-cifs-related/)

Apparently the virtual device was never officially unmounted at shutdown (it did connect one time after first loading NetworkManager.) I have not yet made the change to S<nr>umountnfs.sh to confirm that the sequence adjustment will work after another restart or boot. I want to see what really causes the problem to begin with and am surching log files.

First make sure ndiswrapper has the right driver

$ ndiswrapper -l
wmp54gs : driver installed
    device (14E4:4318) present   ## in my case

Then they suggest the following:

$ cd /etc/rc6.d
$ ls -la

## S<nr>wpa-ifupdown (the nr is probably 15
## and
## S<nr>umountnfs.sh (the nr is probably 31

$ sudo mv S31umountnfs.sh S14umountnfs.sh

## This will give umountnfs.sh an earlier value than wpa-ifupdown.

## Next follow the same steps in /etc/rc0.d

Hope this helps.

---

### Post by j_p36 on 2010-01-27
Sorry it has taken so long to respond to this, I have been very busy with work and have not had time to tinker with my buntu install lately, thank you very much for the tips and I will try them out soon.  On a side note, I installed windows 7 and it overwrote my grub bootloader. Any easy ways to get it back? (I know this isn't the right forum for this but I can't work on my wireless until I can get back into ubuntu and didn't want to start a new topic if this was easy)

---

