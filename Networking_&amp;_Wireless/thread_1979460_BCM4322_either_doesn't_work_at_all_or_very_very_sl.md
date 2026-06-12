---
title: "BCM4322 either doesn't work at all or very very slow on 12.04"
date: 2012-05-13
forum: Networking &amp; Wireless
---

### Post by 9646gt on 2012-05-13
Hopefully someone can help me figure this out. I am running a dual boot of 12.04 and mac os 10.8dp on my macbook model number 5,1. It has the BCM 4322 wireless card it seems. I am very new to linux but I think I have done everything right. I have tried everything I can think of (with my limited knowledge) Including setting ipv6 to "Ignore". Someitmes the card works perfect and the speed test shows 3.5mbps. Other times it shows 0.25mbps or does not work at all but still shows connected. The card works perfect under OSX with no issues at all. I will post the required info below that I found in the how to post a wireless ticket thread. Thanks in advance! Also I am using the 64-bit build.

```
chris@chris-MacBook:~$ lspci
00:00.0 Host bridge: NVIDIA Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: NVIDIA Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: NVIDIA Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
00:03.4 RAM memory: NVIDIA Corporation Device 0a98 (rev b1)
00:03.5 Co-processor: NVIDIA Corporation MCP79 Co-processor (rev b1)
00:04.0 USB controller: NVIDIA Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB controller: NVIDIA Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB controller: NVIDIA Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB controller: NVIDIA Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: NVIDIA Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: NVIDIA Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: NVIDIA Corporation MCP79 Ethernet (rev b1)
00:0b.0 IDE interface: NVIDIA Corporation MCP79 SATA Controller (rev b1)
00:10.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
02:00.0 VGA compatible controller: NVIDIA Corporation C79 [GeForce 9400M] (rev b1)
03:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
chris@chris-MacBook:~$ 

```

```
chris@chris-MacBook:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:df:7b:35:64  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::223:dfff:fe7b:3564/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4467 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3792 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4372534 (4.3 MB)  TX bytes:382523 (382.5 KB)
          Interrupt:42 Base address:0x6000 

eth2      Link encap:Ethernet  HWaddr 00:23:6c:81:6d:cd  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::223:6cff:fe81:6dcd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:270 errors:0 dropped:0 overruns:0 frame:191177
          TX packets:789 errors:16 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:41964 (41.9 KB)  TX bytes:71069 (71.0 KB)
          Interrupt:23 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:726 errors:0 dropped:0 overruns:0 frame:0
          TX packets:726 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:73885 (73.8 KB)  TX bytes:73885 (73.8 KB)

chris@chris-MacBook:~$ 

```

```
chris@chris-MacBook:~$ iwconfig
lo        no wireless extensions.

eth2      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:224  Noise level:169
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.

chris@chris-MacBook:~$ 

```
```
chris@chris-MacBook:~$ lsmod
Module                  Size  Used by
vesafb                 13844  1 
snd_hda_codec_realtek   223867  1 
bnep                   18281  2 
rfcomm                 47604  0 
parport_pc             32866  0 
ppdev                  17113  0 
snd_hda_intel          33773  2 
snd_hda_codec         127706  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  2 snd_hda_intel,snd_hda_codec
lib80211_crypt_tkip    17390  0 
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
joydev                 17693  0 
hid_apple              13375  0 
nvidia              12336440  42 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
applesmc               19554  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
input_polldev          13896  1 applesmc
btusb                  18288  1 
wl                   2568210  0 
bluetooth             180104  13 bnep,rfcomm,btusb
snd                    78855  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
bcm5974                17399  0 
uvcvideo               72627  0 
usbhid                 47199  0 
soundcore              15091  1 snd
videodev               98259  1 uvcvideo
lib80211               14381  2 lib80211_crypt_tkip,wl
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
shpchp                 37277  0 
v4l2_compat_ioctl32    17128  1 videodev
hid                    99559  2 hid_apple,usbhid
i2c_nforce2            13058  0 
apple_bl               13673  0 
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
forcedeth              63460  0 
chris@chris-MacBook:~$ 

```dmesg - I think some got cut off

```
[    0.375457] libata version 3.00 loaded.
[    0.375528] usbcore: registered new interface driver usbfs
[    0.375542] usbcore: registered new interface driver hub
[    0.375580] usbcore: registered new device driver usb
[    0.375714] PCI: Using ACPI for IRQ routing
[    0.377778] PCI: pci_cache_line_size set to 64 bytes
[    0.378045] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.378048] reserve RAM buffer: 00000000be86e000 - 00000000bfffffff 
[    0.378190] NetLabel: Initializing
[    0.378193] NetLabel:  domain hash size = 128
[    0.378195] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.378211] NetLabel:  unlabeled traffic allowed by default
[    0.378273] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.378281] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31, 31
[    0.378288] hpet0: 4 comparators, 64-bit 25.000000 MHz counter
[    0.384083] Switching to clocksource hpet
[    0.394721] AppArmor: AppArmor Filesystem Enabled
[    0.394765] pnp: PnP ACPI init
[    0.394793] ACPI: bus type pnp registered
[    0.394932] pnp 00:00: [bus 00-ff]
[    0.394936] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.394940] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.394943] pnp 00:00: [io  0x0d00-0xffff window]
[    0.394946] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.394949] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.394953] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.394956] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.394959] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.394962] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.394966] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.394969] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.394972] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.394975] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.394979] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.394982] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.394985] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.394988] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.394992] pnp 00:00: [mem 0xc0000000-0xfebfffff window]
[    0.395116] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.395144] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.395147] pnp 00:01: [mem 0xf0000000-0xf3ffffff]
[    0.395220] system 00:01: [mem 0xf0000000-0xf3ffffff] has been reserved
[    0.395225] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.395242] pnp 00:02: [io  0x0300-0x031f]
[    0.395258] pnp 00:02: [irq 6]
[    0.395296] pnp 00:02: Plug and Play ACPI device, IDs APP0001 (active)
[    0.395351] pnp 00:03: [io  0x0000-0x0008]
[    0.395354] pnp 00:03: [io  0x000a-0x000f]
[    0.395356] pnp 00:03: [io  0x0081-0x0083]
[    0.395359] pnp 00:03: [io  0x0087]
[    0.395361] pnp 00:03: [io  0x0089-0x008b]
[    0.395364] pnp 00:03: [io  0x008f]
[    0.395367] pnp 00:03: [io  0x00c0-0x00d1]
[    0.395369] pnp 00:03: [io  0x00d4-0x00df]
[    0.395372] pnp 00:03: [dma 4]
[    0.395414] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.395497] pnp 00:04: [irq 0 disabled]
[    0.395505] pnp 00:04: [irq 8]
[    0.395508] pnp 00:04: [mem 0xfed00000-0xfed003ff]
[    0.395572] system 00:04: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.395577] system 00:04: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.395593] pnp 00:05: [io  0x00f0-0x00f1]
[    0.395600] pnp 00:05: [irq 13]
[    0.395643] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.395794] pnp 00:06: [io  0x0400-0x047f]
[    0.395801] pnp 00:06: [io  0x0480-0x04ff]
[    0.395804] pnp 00:06: [io  0x0500-0x057f]
[    0.395806] pnp 00:06: [io  0x0580-0x05ff]
[    0.395809] pnp 00:06: [io  0x0800-0x087f]
[    0.395812] pnp 00:06: [io  0x0880-0x08ff]
[    0.395814] pnp 00:06: [io  0x2140-0x217f]
[    0.395817] pnp 00:06: [io  0x2100-0x213f]
[    0.395820] pnp 00:06: [io  0x0010-0x001f]
[    0.395823] pnp 00:06: [io  0x0022-0x003f]
[    0.395825] pnp 00:06: [io  0x0044-0x005f]
[    0.395828] pnp 00:06: [io  0x0062-0x0063]
[    0.395831] pnp 00:06: [io  0x0065-0x006f]
[    0.395833] pnp 00:06: [io  0x0072-0x0073]
[    0.395836] pnp 00:06: [io  0x0074-0x007f]
[    0.395839] pnp 00:06: [io  0x0091-0x0093]
[    0.395841] pnp 00:06: [io  0x0097-0x009f]
[    0.395844] pnp 00:06: [io  0x00a2-0x00bf]
[    0.395846] pnp 00:06: [io  0x00e0-0x00ef]
[    0.395849] pnp 00:06: [io  0x04d0-0x04d1]
[    0.395852] pnp 00:06: [io  0x0080]
[    0.395854] pnp 00:06: [io  0x0295-0x0296]
[    0.395931] system 00:06: [io  0x0400-0x047f] has been reserved
[    0.395935] system 00:06: [io  0x0480-0x04ff] has been reserved
[    0.395939] system 00:06: [io  0x0500-0x057f] has been reserved
[    0.395943] system 00:06: [io  0x0580-0x05ff] has been reserved
[    0.395946] system 00:06: [io  0x0800-0x087f] has been reserved
[    0.395950] system 00:06: [io  0x0880-0x08ff] has been reserved
[    0.395954] system 00:06: [io  0x2140-0x217f] has been reserved
[    0.395957] system 00:06: [io  0x2100-0x213f] has been reserved
[    0.395961] system 00:06: [io  0x04d0-0x04d1] has been reserved
[    0.395965] system 00:06: [io  0x0295-0x0296] has been reserved
[    0.395970] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.395982] pnp 00:07: [io  0x0070-0x0077]
[    0.396052] pnp 00:07: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.405742] pnp: PnP ACPI: found 8 devices
[    0.405745] ACPI: ACPI bus type pnp unregistered
[    0.412973] PCI: max bus depth: 1 pci_try_num: 2
[    0.413019] pci 0000:00:09.0: PCI bridge to [bus 01-01]
[    0.413025] pci 0000:00:09.0:   bridge window [mem 0xd3200000-0xd32fffff]
[    0.413034] pci 0000:00:10.0: PCI bridge to [bus 02-02]
[    0.413037] pci 0000:00:10.0:   bridge window [io  0x1000-0x1fff]
[    0.413042] pci 0000:00:10.0:   bridge window [mem 0xd2000000-0xd30fffff]
[    0.413047] pci 0000:00:10.0:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.413053] pci 0000:00:15.0: PCI bridge to [bus 03-03]
[    0.413065] pci 0000:00:15.0:   bridge window [mem 0xd3100000-0xd31fffff]
[    0.413089] pci 0000:00:09.0: enabling device (0000 -> 0002)
[    0.413097] pci 0000:00:09.0: setting latency timer to 64
[    0.413106] pci 0000:00:10.0: setting latency timer to 64
[    0.413311] ACPI: PCI Interrupt Link [Z00F] enabled at IRQ 23
[    0.413328] pci 0000:00:15.0: PCI INT A -> Link[Z00F] -> GSI 23 (level, low) -> IRQ 23
[    0.413339] pci 0000:00:15.0: setting latency timer to 64
[    0.413346] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.413350] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.413353] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.413357] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.413360] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.413364] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.413367] pci_bus 0000:00: resource 10 [mem 0x000d0000-0x000d3fff]
[    0.413370] pci_bus 0000:00: resource 11 [mem 0x000d4000-0x000d7fff]
[    0.413373] pci_bus 0000:00: resource 12 [mem 0x000d8000-0x000dbfff]
[    0.413376] pci_bus 0000:00: resource 13 [mem 0x000dc000-0x000dffff]
[    0.413380] pci_bus 0000:00: resource 14 [mem 0x000e0000-0x000e3fff]
[    0.413383] pci_bus 0000:00: resource 15 [mem 0x000e4000-0x000e7fff]
[    0.413386] pci_bus 0000:00: resource 16 [mem 0x000e8000-0x000ebfff]
[    0.413389] pci_bus 0000:00: resource 17 [mem 0x000ec000-0x000effff]
[    0.413392] pci_bus 0000:00: resource 18 [mem 0x000f0000-0x000fffff]
[    0.413396] pci_bus 0000:00: resource 19 [mem 0xc0000000-0xfebfffff]
[    0.413399] pci_bus 0000:01: resource 1 [mem 0xd3200000-0xd32fffff]
[    0.413404] pci_bus 0000:01: resource 4 [io  0x0000-0x0cf7]
[    0.413408] pci_bus 0000:01: resource 5 [io  0x0d00-0xffff]
[    0.413412] pci_bus 0000:01: resource 6 [mem 0x000a0000-0x000bffff]
[    0.413417] pci_bus 0000:01: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.413421] pci_bus 0000:01: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.413426] pci_bus 0000:01: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.413430] pci_bus 0000:01: resource 10 [mem 0x000d0000-0x000d3fff]
[    0.413435] pci_bus 0000:01: resource 11 [mem 0x000d4000-0x000d7fff]
[    0.413439] pci_bus 0000:01: resource 12 [mem 0x000d8000-0x000dbfff]
[    0.413444] pci_bus 0000:01: resource 13 [mem 0x000dc000-0x000dffff]
[    0.413448] pci_bus 0000:01: resource 14 [mem 0x000e0000-0x000e3fff]
[    0.413453] pci_bus 0000:01: resource 15 [mem 0x000e4000-0x000e7fff]
[    0.413457] pci_bus 0000:01: resource 16 [mem 0x000e8000-0x000ebfff]
[    0.413462] pci_bus 0000:01: resource 17 [mem 0x000ec000-0x000effff]
[    0.413466] pci_bus 0000:01: resource 18 [mem 0x000f0000-0x000fffff]
[    0.413471] pci_bus 0000:01: resource 19 [mem 0xc0000000-0xfebfffff]
[    0.413475] pci_bus 0000:02: resource 0 [io  0x1000-0x1fff]
[    0.413480] pci_bus 0000:02: resource 1 [mem 0xd2000000-0xd30fffff]
[    0.413485] pci_bus 0000:02: resource 2 [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.413490] pci_bus 0000:03: resource 1 [mem 0xd3100000-0xd31fffff]
[    0.413544] NET: Registered protocol family 2
[    0.413860] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.415688] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.420572] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.421196] TCP: Hash tables configured (established 524288 bind 65536)
[    0.421199] TCP reno registered
[    0.421220] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.421314] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.421518] NET: Registered protocol family 1
[    0.421821] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 22
[    0.421849] pci 0000:00:04.0: PCI INT A -> Link[LUS0] -> GSI 22 (level, low) -> IRQ 22
[    0.492047] pci 0000:00:04.0: PCI INT A disabled
[    0.492284] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 21
[    0.492306] pci 0000:00:04.1: PCI INT B -> Link[LUS2] -> GSI 21 (level, low) -> IRQ 21
[    0.492344] pci 0000:00:04.1: PCI INT B disabled
[    0.492517] ACPI: PCI Interrupt Link [Z000] enabled at IRQ 20
[    0.492528] pci 0000:00:06.0: PCI INT A -> Link[Z000] -> GSI 20 (level, low) -> IRQ 20
[    0.548046] pci 0000:00:06.0: PCI INT A disabled
[    0.548281] ACPI: PCI Interrupt Link [Z001] enabled at IRQ 19
[    0.548307] pci 0000:00:06.1: PCI INT B -> Link[Z001] -> GSI 19 (level, low) -> IRQ 19
[    0.548344] pci 0000:00:06.1: PCI INT B disabled
[    0.548428] pci 0000:02:00.0: Boot video device
[    0.548591] PCI: CLS 256 bytes, default 64
[    0.548596] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.548599] Placing 64MB software IO TLB between ffff8800ba864000 - ffff8800be864000
[    0.548602] software IO TLB at phys 0xba864000 - 0xbe864000
[    0.549067] audit: initializing netlink socket (disabled)
[    0.549083] type=2000 audit(1336925263.544:1): initialized
[    0.549519] Freeing initrd memory: 13840k freed
[    0.604090] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.655344] VFS: Disk quotas dquot_6.5.2
[    0.655425] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.656179] fuse init (API version 7.17)
[    0.656311] msgmni has been set to 15415
[    0.656780] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.656820] io scheduler noop registered
[    0.656823] io scheduler deadline registered
[    0.656871] io scheduler cfq registered (default)
[    0.657043] pcieport 0000:00:15.0: setting latency timer to 64
[    0.657186] pcieport 0000:00:15.0: irq 40 for MSI/MSI-X
[    0.657395] pcieport 0000:00:15.0: Signaling PME through PCIe PME interrupt
[    0.657399] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    0.657408] pcie_pme 0000:00:15.0:pcie01: service driver pcie_pme loaded
[    0.657431] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.657462] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.657535] efifb: dmi detected MacBook5,1 - framebuffer at 0xd1000000 (640x480, stride 2560)
[    0.657539] intel_idle: MWAIT substates: 0x3122220
[    0.657541] intel_idle: does not run on family 6 model 23
[    0.657597] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.657654] ACPI: AC Adapter [ADP1] (on-line)
[    0.657806] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.657829] ACPI: Lid Switch [LID0]
[    0.657888] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.657894] ACPI: Power Button [PWRB]
[    0.657952] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.657957] ACPI: Sleep Button [SLPB]
[    0.658049] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.658053] ACPI: Power Button [PWRF]
[    0.658239] Monitor-Mwait will be used to enter C-1 state
[    0.658276] Monitor-Mwait will be used to enter C-2 state
[    0.658311] Monitor-Mwait will be used to enter C-3 state
[    0.658320] Marking TSC unstable due to TSC halts in idle
[    0.658337] ACPI: acpi_idle registered with cpuidle
[    0.664027] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.664042] ACPI: Battery Slot [BAT0] (battery present)
[    0.664084] ERST: Table is not found!
[    0.664086] GHES: HEST is not enabled!
[    0.664227] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.771927] ACPI: Battery Slot [BAT0] (battery present)
[    0.820374] Linux agpgart interface v0.103
[    0.822473] brd: module loaded
[    0.823578] loop: module loaded
[    0.823753] ahci 0000:00:0b.0: version 3.0
[    0.823942] ACPI: PCI Interrupt Link [LSI0] enabled at IRQ 18
[    0.823957] ahci 0000:00:0b.0: PCI INT A -> Link[LSI0] -> GSI 18 (level, low) -> IRQ 18
[    0.824031] ahci 0000:00:0b.0: irq 41 for MSI/MSI-X
[    0.824039] ahci 0000:00:0b.0: controller can't do PMP, turning off CAP_PMP
[    0.824095] ahci 0000:00:0b.0: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3 impl IDE mode
[    0.824100] ahci 0000:00:0b.0: flags: 64bit ncq sntf pm led pio slum part boh 
[    0.824105] ahci 0000:00:0b.0: setting latency timer to 64
[    0.824945] scsi0 : ahci
[    0.825059] scsi1 : ahci
[    0.825157] scsi2 : ahci
[    0.825260] scsi3 : ahci
[    0.825368] scsi4 : ahci
[    0.825474] scsi5 : ahci
[    0.825654] ata1: SATA max UDMA/133 abar m8192@0xd3384000 port 0xd3384100 irq 41
[    0.825658] ata2: SATA max UDMA/133 abar m8192@0xd3384000 port 0xd3384180 irq 41
[    0.825661] ata3: DUMMY
[    0.825663] ata4: DUMMY
[    0.825665] ata5: DUMMY
[    0.825666] ata6: DUMMY
[    0.826162] Fixed MDIO Bus: probed
[    0.826190] tun: Universal TUN/TAP device driver, 1.6
[    0.826193] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.826265] PPP generic driver version 2.4.2
[    0.826408] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.826432] ehci_hcd 0000:00:04.1: PCI INT B -> Link[LUS2] -> GSI 21 (level, low) -> IRQ 21
[    0.826451] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    0.826455] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    0.826523] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 1
[    0.826550] ehci_hcd 0000:00:04.1: debug port 1
[    0.826559] ehci_hcd 0000:00:04.1: cache line size of 256 is not supported
[    0.826578] ehci_hcd 0000:00:04.1: irq 21, io mem 0xd3389200
[    0.836018] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    0.836204] hub 1-0:1.0: USB hub found
[    0.836210] hub 1-0:1.0: 7 ports detected
[    0.836304] ehci_hcd 0000:00:06.1: PCI INT B -> Link[Z001] -> GSI 19 (level, low) -> IRQ 19
[    0.836320] ehci_hcd 0000:00:06.1: setting latency timer to 64
[    0.836324] ehci_hcd 0000:00:06.1: EHCI Host Controller
[    0.836397] ehci_hcd 0000:00:06.1: new USB bus registered, assigned bus number 2
[    0.836417] ehci_hcd 0000:00:06.1: debug port 1
[    0.836426] ehci_hcd 0000:00:06.1: cache line size of 256 is not supported
[    0.836447] ehci_hcd 0000:00:06.1: irq 19, io mem 0xd3389100
[    0.848021] ehci_hcd 0000:00:06.1: USB 2.0 started, EHCI 1.00
[    0.848184] hub 2-0:1.0: USB hub found
[    0.848190] hub 2-0:1.0: 5 ports detected
[    0.848280] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.848298] ohci_hcd 0000:00:04.0: PCI INT A -> Link[LUS0] -> GSI 22 (level, low) -> IRQ 22
[    0.848314] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    0.848318] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    0.848384] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 3
[    0.848410] ohci_hcd 0000:00:04.0: irq 22, io mem 0xd3388000
[    0.906152] hub 3-0:1.0: USB hub found
[    0.906159] hub 3-0:1.0: 7 ports detected
[    0.906247] ohci_hcd 0000:00:06.0: PCI INT A -> Link[Z000] -> GSI 20 (level, low) -> IRQ 20
[    0.906263] ohci_hcd 0000:00:06.0: setting latency timer to 64
[    0.906267] ohci_hcd 0000:00:06.0: OHCI Host Controller
[    0.906329] ohci_hcd 0000:00:06.0: new USB bus registered, assigned bus number 4
[    0.906354] ohci_hcd 0000:00:06.0: irq 20, io mem 0xd3387000
[    0.962156] hub 4-0:1.0: USB hub found
[    0.962163] hub 4-0:1.0: 5 ports detected
[    0.962246] uhci_hcd: USB Universal Host Controller Interface driver
[    0.962319] usbcore: registered new interface driver libusual
[    0.962368] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.963227] i8042: No controller found
[    0.963329] mousedev: PS/2 mouse device common for all mice
[    0.963833] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    0.963885] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    0.963985] device-mapper: uevent: version 1.0.3
[    0.964096] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    0.964181] cpuidle: using governor ladder
[    0.964302] cpuidle: using governor menu
[    0.964304] EFI Variables Facility v0.08 2004-May-17
[    0.964622] TCP cubic registered
[    0.964763] NET: Registered protocol family 10
[    0.965381] NET: Registered protocol family 17
[    0.965402] Registering the dns_resolver key type
[    0.965614] PM: Hibernation image not present or could not be loaded.
[    0.965631] registered taskstats version 1
[    0.999129]   Magic number: 12:730:135
[    0.999170] block ram0: hash matches
[    0.999208] pci 0000:00:03.1: hash matches
[    0.999303] rtc_cmos 00:07: setting system clock to 2012-05-13 16:07:44 UTC (1336925264)
[    0.999852] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.999854] EDD information not available.
[    1.144108] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.144128] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.144571] ata1.00: ATA-8: FUJITSU MHZ2250BH FFS G1, 0081008C, max UDMA/100
[    1.144575] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.145188] ata1.00: configured for UDMA/100
[    1.145351] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHZ2250B 0081 PQ: 0 ANSI: 5
[    1.145477] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.145492] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.145524] sd 0:0:0:0: [sda] Write Protect is off
[    1.145527] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.145548] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.148045] usb 1-4: new high-speed USB device number 2 using ehci_hcd
[    1.148224] ata2.00: ATAPI: HL-DT-ST DVDRW  GS21N, SA18, max UDMA/133
[    1.152984] ata2.00: configured for UDMA/133
[    1.158472] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRW  GS21N     SA18 PQ: 0 ANSI: 5
[    1.163441] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda caddy
[    1.163444] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.163591] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.163673] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.223494]  sda: sda1 sda2 sda3 sda4 sda5
[    1.224092] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.225636] Freeing unused kernel memory: 920k freed
[    1.225902] Write protecting the kernel read-only data: 12288k
[    1.231139] Freeing unused kernel memory: 1608k freed
[    1.235433] Freeing unused kernel memory: 1196k freed
[    1.250497] udevd[102]: starting version 175
[    1.341447] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.341625] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 17
[    1.341640] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 17 (level, low) -> IRQ 17
[    1.341646] forcedeth 0000:00:0a.0: setting latency timer to 64
[    1.413180] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:23:df:7b:35:64
[    1.413185] forcedeth 0000:00:0a.0: highdma csum pwrctl gbit lnktim msi desc-v3
[    1.749410] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    1.888130] usb 4-1: new full-speed USB device number 2 using ohci_hcd
[    2.113156] hub 4-1:1.0: USB hub found
[    2.116047] hub 4-1:1.0: 3 ports detected
[    2.432101] usb 3-5: new low-speed USB device number 2 using ohci_hcd
[    2.956128] usb 3-6: new full-speed USB device number 3 using ohci_hcd
[    3.270048] usb 4-1.1: new full-speed USB device number 3 using ohci_hcd
[   13.006480] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.023412] udevd[359]: starting version 175
[   13.048917] lp: driver loaded but no devices found
[   13.064681] Adding 1049596k swap on /dev/sda4.  Priority:-1 extents:1 across:1049596k 
[   13.236530] i2c i2c-0: nForce2 SMBus adapter at 0x2140
[   13.238073] i2c i2c-1: nForce2 SMBus adapter at 0x2100
[   13.243409] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.270414] lib80211: common routines for IEEE802.11 drivers
[   13.270418] lib80211_crypt: registered algorithm 'NULL'
[   13.272553] Linux video capture interface: v2.00
[   13.273130] usbcore: registered new interface driver usbhid
[   13.273133] usbhid: USB HID core driver
[   13.273440] uvcvideo: Found UVC 1.00 device Built-in iSight (05ac:8507)
[   13.287226] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   13.297788] nvidia: module license 'NVIDIA' taints kernel.
[   13.297792] Disabling lock debugging due to kernel taint
[   13.313005] type=1400 audit(1336925276.810:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=619 comm="apparmor_parser"
[   13.313447] type=1400 audit(1336925276.810:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=619 comm="apparmor_parser"
[   13.313678] type=1400 audit(1336925276.810:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=619 comm="apparmor_parser"
[   13.322071] input: bcm5974 as /devices/pci0000:00/0000:00:04.0/usb3/3-6/3-6:1.2/input/input4
[   13.324486] input: Built-in iSight as /devices/pci0000:00/0000:00:04.1/usb1/1-4/1-4:1.0/input/input5
[   13.330295] usbcore: registered new interface driver uvcvideo
[   13.330298] USB Video Class driver (1.1.1)
[   13.330940] usbcore: registered new interface driver bcm5974
[   13.372901] wl 0000:03:00.0: power state changed by ACPI to D0
[   13.372908] wl 0000:03:00.0: power state changed by ACPI to D0
[   13.372919] wl 0000:03:00.0: PCI INT A -> Link[Z00F] -> GSI 23 (level, low) -> IRQ 23
[   13.372926] wl 0000:03:00.0: setting latency timer to 64
[   13.395680] Bluetooth: Core ver 2.16
[   13.395721] NET: Registered protocol family 31
[   13.395723] Bluetooth: HCI device and connection manager initialized
[   13.395726] Bluetooth: HCI socket layer initialized
[   13.395728] Bluetooth: L2CAP socket layer initialized
[   13.395734] Bluetooth: SCO socket layer initialized
[   13.424284] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   13.456971] usbcore: registered new interface driver btusb
[   13.578723] ACPI: PCI Interrupt Link [LPMU] enabled at IRQ 16
[   13.578738] nvidia 0000:00:03.5: PCI INT B -> Link[LPMU] -> GSI 16 (level, low) -> IRQ 16
[   13.578748] nvidia: probe of 0000:00:03.5 failed with error -1
[   13.578876] ACPI: PCI Interrupt Link [LGPU] enabled at IRQ 23
[   13.578880] nvidia 0000:02:00.0: PCI INT A -> Link[LGPU] -> GSI 23 (level, low) -> IRQ 23
[   13.578886] nvidia 0000:02:00.0: setting latency timer to 64
[   13.578890] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   13.584574] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  295.49  Mon Apr 30 23:46:33 PDT 2012
[   13.631608] apple 0003:05AC:8242.0001: hiddev0,hidraw0: USB HID v1.11 Device [Apple Computer, Inc. IR Receiver] on usb-0000:00:04.0-5/input0
[   13.647109] input: Apple, Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:04.0/usb3/3-6/3-6:1.0/input/input6
[   13.648164] apple 0003:05AC:0236.0002: input,hidraw1: USB HID v1.11 Keyboard [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:04.0-6/input0
[   13.661167] apple 0003:05AC:0236.0003: hidraw2: USB HID v1.11 Device [Apple, Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:04.0-6/input1
[   13.667367] lib80211_crypt: registered algorithm 'TKIP'
[   13.729023] eth1: Broadcom BCM432b 802.11 Hybrid Wireless Controller 5.100.82.38
[   13.731291] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 22
[   13.731297] snd_hda_intel 0000:00:08.0: PCI INT A -> Link[LAZA] -> GSI 22 (level, low) -> IRQ 22
[   13.731300] hda_intel: Disabling MSI
[   13.731330] snd_hda_intel 0000:00:08.0: setting latency timer to 64
[   13.849817] udevd[369]: renamed network interface eth1 to eth2
[   13.888022] applesmc: key=271 fan=1 temp=14 acc=1 lux=2 kbd=1
[   13.944455] input: applesmc as /devices/platform/applesmc.768/input/input7
[   13.944637] Registered led device: smc::kbd_backlight
[   13.946301] init: failsafe main process (843) killed by TERM signal
[   14.198962] ppdev: user-space parallel port driver
[   14.333940] Bluetooth: RFCOMM TTY layer initialized
[   14.333946] Bluetooth: RFCOMM socket layer initialized
[   14.333948] Bluetooth: RFCOMM ver 1.11
[   14.343686] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.343689] Bluetooth: BNEP filters: protocol multicast
[   14.351513] type=1400 audit(1336925277.846:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=942 comm="apparmor_parser"
[   14.351966] type=1400 audit(1336925277.846:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=942 comm="apparmor_parser"
[   14.373754] hda_codec: ALC889A: SKU not ready 0x400000f0
[   14.376554] type=1400 audit(1336925277.874:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=975 comm="apparmor_parser"
[   14.377069] type=1400 audit(1336925277.874:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=974 comm="apparmor_parser"
[   14.379018] type=1400 audit(1336925277.874:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=975 comm="apparmor_parser"
[   14.379232] type=1400 audit(1336925277.874:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=975 comm="apparmor_parser"
[   14.383136] type=1400 audit(1336925277.878:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=978 comm="apparmor_parser"
[   14.428956] forcedeth 0000:00:0a.0: irq 42 for MSI/MSI-X
[   14.429151] forcedeth 0000:00:0a.0: eth0: no link during initialization
[   14.430296] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.430842] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.383031] vesafb: mode is 640x480x32, linelength=2560, pages=0
[   15.383034] vesafb: scrolling: redraw
[   15.383036] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   15.385779] vesafb: framebuffer at 0xd1000000, mapped to 0xffffc90005a80000, using 1216k, total 1216k
[   15.386311] Console: switching to colour frame buffer device 80x30
[   15.386324] fb0: VESA VGA frame buffer device
[   51.568040] eth2: no IPv6 routers present
[  255.185452] forcedeth 0000:00:0a.0: eth0: link up
[  255.187173] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  265.648042] eth0: no IPv6 routers present
chris@chris-MacBook:~$ 

```
```
chris@chris-MacBook:~$ sudo lshw -C network
[sudo] password for chris: 
  *-network               
       description: Ethernet interface
       product: MCP79 Ethernet
       vendor: NVIDIA Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: b1
       serial: 00:23:df:7b:35:64
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.0.2 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 memory:d3386000-d3386fff ioport:21e0(size=8) memory:d3389000-d33890ff memory:d3389300-d338930f
  *-network
       description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth2
       version: 01
       serial: 00:23:6c:81:6d:cd
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 ip=192.168.0.4 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:23 memory:d3100000-d3103fff
chris@chris-MacBook:~$ 

```
```
chris@chris-MacBook:~$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ] 
chris@chris-MacBook:~$ 

```

---

### Post by chili555 on 2012-05-13
First, there are several devices that are claimed by both wl and b43 as well as more Broadcom drivers. Lets be sure your card has the right driver. Please post:```
lspci -nn | grep 0280
```Second, I see that both wired and wireless are connected and have an IP address. It is confusing to your system and hard to diagnose a problem when there are two network connections. Please detach the ethernet.

---

### Post by 9646gt on 2012-05-13
> **chili555 said:**
> First, there are several devices that are claimed by both wl and b43 as well as more Broadcom drivers. Lets be sure your card has the right driver. Please post:```
lspci -nn | grep 0280
```Second, I see that both wired and wireless are connected and have an IP address. It is confusing to your system and hard to diagnose a problem when there are two network connections. Please detach the ethernet.

```
chris@chris-MacBook:~$ lspci -nn | grep 0280
03:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
chris@chris-MacBook:~$ 

```

There ya go! Thanks for the quick reply! Hopefully you can make something of this and I can learn something as well. I should note that I am doing these posts while connected to a wired connection. However my wifi also still says it is connected as well. Is it ok for me to run the commands in terminal connected only to wifi and then reconnect my wired connection to update the post on here?

---

### Post by 9646gt on 2012-05-13
Ok, so. This may not have anything to do with my issue. And it may still mess up but so far so good. I originally had my router set not to broadcast the ssid. I changed it to broadcast and use wpa2 security and now all seems well. But this may just be good luck lol. Also it seems from the last reply I may still have further issues. If so I would still like to resolve those :)

---

### Post by chili555 on 2012-05-13
The driver that's loaded, wl is correct for your device. the driver combination b43 and ssb that conflict are not loaded and evidently are correctly blacklisted. Please detach the ethernet cable, reboot and show me:```
iwconfig
dmesg | grep -e wl -e eth1
```Is your router set to B and G or B, G and N speeds? WPA2 only or the dreaded and tricky WPA and WPA2 mixed mode?```
sudo iwlist eth1 scan
```

---

### Post by 9646gt on 2012-05-13
```
chris@chris-MacBook:~$ iwconfig
lo        no wireless extensions.

eth2      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:213  Noise level:170
          Rx invalid nwid:0  invalid crypt:3  invalid misc:0

eth0      no wireless extensions.

chris@chris-MacBook:~$ 

```

```
chris@chris-MacBook:~$ dmesg | grep -e wl -e eth1
[   13.346338] wl 0000:03:00.0: power state changed by ACPI to D0
[   13.346345] wl 0000:03:00.0: power state changed by ACPI to D0
[   13.346356] wl 0000:03:00.0: PCI INT A -> Link[Z00F] -> GSI 23 (level, low) -> IRQ 23
[   13.346363] wl 0000:03:00.0: setting latency timer to 64
[   13.646190] eth1: Broadcom BCM432b 802.11 Hybrid Wireless Controller 5.100.82.38
[   13.901764] udevd[374]: renamed network interface eth1 to eth2
chris@chris-MacBook:~$
```
```
chris@chris-MacBook:~$ sudo iwlist eth1 scan
[sudo] password for chris: 
eth1      Interface doesn't support scanning.

chris@chris-MacBook:~$
```

The router is a dslmodem/wireless router combo from my provider. It is set up for b and g speeds and security is only wpa2. All those results are from a fresh reboot running off wifi. The connection still seems perfect so far with no issues. But still willing to make any corrections if needed :)

---

### Post by chili555 on 2012-05-14
>  udevd[374]: renamed network interface eth1 to eth2Did you have some other wireless device previously? We might tweak a file or two and remove all references to it. I'm not sure it has much to do with speed, but it's a bit cleaner.> This may not have anything to do with my issue. And it may still mess up but so far so good. I originally had my router set *not to broadcast the ssid*. I changed it to broadcast and use wpa2 security and now all seems well.That could very well be the issue. I suggest you continue to monitor and post back if it's not fixed.

---

### Post by 9646gt on 2012-05-14
This morning I am again experiencing terrible performance. I ran one of the commands you spoke of earier hoping it would help.


chris@chris-MacBook:~$ dmesg | grep -e wl -e eth1
[   13.346338] wl 0000:03:00.0: power state changed by ACPI to D0
[   13.346345] wl 0000:03:00.0: power state changed by ACPI to D0
[   13.346356] wl 0000:03:00.0: PCI INT A -> Link[Z00F] -> GSI 23 (level, low) -> IRQ 23
[   13.346363] wl 0000:03:00.0: setting latency timer to 64
[   13.646190] eth1: Broadcom BCM432b 802.11 Hybrid Wireless Controller 5.100.82.38
[   13.901764] udevd[374]: renamed network interface eth1 to eth2
[ 2601.478073] wl 0000:03:00.0: PCI INT A disabled
[ 2601.492331] wl 0000:03:00.0: power state changed by ACPI to D3
[ 2603.117309] wl 0000:03:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[ 2603.117325] wl 0000:03:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xd3100004)
[ 2603.117329] wl 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x40)
[ 2603.117335] wl 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
[ 2603.118759] wl 0000:03:00.0: power state changed by ACPI to D0
[ 2603.118765] wl 0000:03:00.0: power state changed by ACPI to D0
[ 2603.118772] wl 0000:03:00.0: power state changed by ACPI to D0
[ 2603.118777] wl 0000:03:00.0: power state changed by ACPI to D0
[ 2603.118785] wl 0000:03:00.0: PCI INT A -> Link[Z00F] -> GSI 23 (level, low) -> IRQ 23
[ 2603.118793] wl 0000:03:00.0: setting latency timer to 64
chris@chris-MacBook:~$

---

### Post by 9646gt on 2012-05-14
Ok so the terrible performance is now back to normal. I just disconnected and reconnected to my network. After that it took a couple minutes for performance to come back. Odd.

---

### Post by chili555 on 2012-05-14
All the entries in dmesg with 13.xx timestamps are during bootup. All the 2603.xx are much later. I wonder if this has to do with power management. Let's try to turn it off and see if there is an improvement:```
sudo iwconfig eth2 power off
```Any errors or warnings? Any improvement?

---

### Post by 9646gt on 2012-05-14
Currently at work right now. I will post back when I get home and can test her out again with the command you gave. thanks for the continued support!

---

### Post by 9646gt on 2012-05-14
Also, just to be sure. What am I checking after I do the power off command? If it reports no errors, do you want me to give it the power on command and see how the speed does?

---

### Post by chili555 on 2012-05-14
> **9646gt said:**
> Also, just to be sure. What am I checking after I do the power off command? If it reports no errors, do you want me to give it the power on command and see how the speed does?It may produce an error; essentially, 'sorry, power management is not changeable by users.' If it comes back with no error, then power management is off. That means the card will not try to power down when it thinks there is no activity, such as mouse/keyboard/touchpad. What we are hoping is that turning off this feature (??) will make the card operate with more stability. Just monitor things and see what happens. If it works, we'll permanently turn power management off.

---

### Post by 9646gt on 2012-05-14
Ok I ran it and it gave no errors or other messages at all. I will continue using the computer and see what happens. If I close the lid or anything will I need to re-enable this command or should it work till the computer is restarted?

---

### Post by chili555 on 2012-05-14
It should work until the computer is restarted. If it works to correct the slow-downs, we can tweak one file to make it persistent; that is, automatic after reboot.

---

### Post by 9646gt on 2012-05-14
ok, so I unplugged the computer after it sat about an hour plugged in with the lid open. I started using it and the conection was terrible. As soon as I ran the command again it seemed to instantly come back to life. It seems like the power saving is getting turned back on again automatically. Looks like we need to fix that issue I guess.

---

### Post by chili555 on 2012-05-14
> It seems like the power saving is getting turned back on again automatically.Is it? What does this tell us?```
iwconfig eth2
sudo iw eth2 get power_save
```

---

### Post by 9646gt on 2012-05-14
chris@chris-MacBook:~$ iwconfig eth2
eth2      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:210  Noise level:170
          Rx invalid nwid:0  invalid crypt:171  invalid misc:0

chris@chris-MacBook:~$ sudo iw eth2 get power_save
[sudo] password for chris: 
nl80211 not found.
chris@chris-MacBook:~$

---

### Post by chili555 on 2012-05-14
> chris@chris-MacBook:~$ sudo iw eth2 get power_save
[sudo] password for chris:
nl80211 not found.Verrrry interesting. Let's try the old-school way:```
sudo iwlist eth2 power
```

---

### Post by 9646gt on 2012-05-14
chris@chris-MacBook:~$ sudo iwlist eth2 power
[sudo] password for chris: 
eth2      Current mode:off

chris@chris-MacBook:~$

---

### Post by chili555 on 2012-05-14
I'm getting low on ideas. Is the router set to B and G speeds or B, G and N? Some drivers have trouble with N.

This is an admitted long shot, but how about:```
dmesg | grep -e wl -e eth 
```Usually, the wl module is rock-steady.

I don't quite understand this:> $ iwconfig eth2
eth2 IEEE 802.11 Access Point: Not-Associated
[COLOR="Red"]Link Quality:5[/COLOR] Signal level:210 Noise level:170
Rx invalid nwid:0 invalid crypt:171 invalid misc:0
I have most often seen this as a fraction like 62/70.

---

### Post by 9646gt on 2012-05-14
```
chris@chris-MacBook:~$ dmesg | grep -e wl -e eth
[    0.165779] Apple MacBook5 series board detected. Selecting PCI-method for reboots.
[    0.375274] i2c-core: driver [aat2870] using legacy suspend method
[    0.375276] i2c-core: driver [aat2870] using legacy resume method
[    1.312583] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.312779] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 17 (level, low) -> IRQ 17
[    1.312785] forcedeth 0000:00:0a.0: setting latency timer to 64
[    1.377196] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:23:df:7b:35:64
[    1.377200] forcedeth 0000:00:0a.0: highdma csum pwrctl gbit lnktim msi desc-v3
[   13.085358] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.310874] wl: module license 'MIXED/Proprietary' taints kernel.
[   13.348271] wl 0000:03:00.0: power state changed by ACPI to D0
[   13.348278] wl 0000:03:00.0: power state changed by ACPI to D0
[   13.348289] wl 0000:03:00.0: PCI INT A -> Link[Z00F] -> GSI 23 (level, low) -> IRQ 23
[   13.348296] wl 0000:03:00.0: setting latency timer to 64
[   13.426503] eth1: Broadcom BCM432b 802.11 Hybrid Wireless Controller 5.100.82.38
[   13.869343] udevd[386]: renamed network interface eth1 to eth2
[   14.519618] forcedeth 0000:00:0a.0: irq 42 for MSI/MSI-X
[   14.519814] forcedeth 0000:00:0a.0: eth0: no link during initialization
[   14.520984] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.521430] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   54.896149] eth2: no IPv6 routers present
chris@chris-MacBook:~$ 

```


The router is set to just b&g only. I did all the steps listed in the following link and so far no issues. But will report back if the good luck continues over the next couple hours lol
[http://www.unixmen.com/resolve-slow-connexion-when-using-wifi-in-ubuntu-1104-natty-narwhal/](http://www.unixmen.com/resolve-slow-connexion-when-using-wifi-in-ubuntu-1104-natty-narwhal/)

---

### Post by chili555 on 2012-05-14
> I did all the steps listed in the following link and so far no issues.I hope you only did the third method. The first two have no effect to you because your driver is not ath9k nor the now obsolete iwlagn; it is wl.

There are much easier ways to disable IPv6.

Let's see how it goes.

---

### Post by 9646gt on 2012-05-14
Nope didn't do number 3 as I disabled ipv6 in the connections manager. Just did the first two.

---

### Post by 9646gt on 2012-05-15
Performed a restart last and had another slow buggy connection. One I turned power save back off as you said, it got better almost instantly. Is there a way to keep power saving mode turned off altogether?

---

### Post by chili555 on 2012-05-15
> Nope didn't do number 3 as I disabled ipv6 in the connections manager. Just did the first two.They are meaningless because you don't have either of those drivers. You may as well remove those two files:```
sudo rm /etc/modprobe.d/ath9k.conf
sudo rm /etc/modprobe.d/iwlagn-disable11n.conf
```It is unfortunate that faulty tutorials get written and, moreover, in a few months become obsolete. I'm sure many a new user has followed them and found no fix. I will contact the original author.> Is there a way to keep power saving mode turned off altogether? Please try this:```
sudo gedit /etc/rc.local
```Add a line above exit 0:```
iwconfig eth2 power off
```Proofread carefully, save and close gedit.

---

### Post by 9646gt on 2012-05-15
Applied the changes. Thanks a ton for your awesome help. I will keep this post updated! Thanks again! So glad I chose a distro with such good community support!

---

### Post by chili555 on 2012-05-15
I'm glad it's working. Thank you for your kind words.

---

### Post by 9646gt on 2012-05-15
Ok So posting back. My connection dropped something terrible again today. I did a little test. I started a speed test at speedtest.net. It was at like 0.15mbps. The INSTANT I did the sudo iwconfig eth2 power off command in terminal the speed test shot up to aroun 7.0mbps. Is there a way we can make a script or something that will run the command every couple of minutes?

---

### Post by 9646gt on 2012-05-18
Please try this:```
sudo gedit /etc/rc.local
```Add a line above exit 0:```
iwconfig eth2 power off
```Proofread carefully, save and close gedit.[/QUOTE]
 
It seems that power saving mode has managed to turn itself back on again using that fix. I will sometimes have a terrible slow connection but as soon as I manually turn off power saving again it fixes it. Can I not make a script to re-run the command every so often without having to manually do it each time?

---

### Post by chili555 on 2012-05-18
A few very interesting comments here: [http://audal.nial.se/networkmanager](http://audal.nial.se/networkmanager) and here: [http://audal.nial.se/bcmwl](http://audal.nial.se/bcmwl)> If the above works for a while and then latency issues come back you can use cron to do it once a minute. Edit cron with the crontab command: (Yeah, I really should hunt the real issue down but I have no idea how.) Also check here: [https://bugzilla.gnome.org/show_bug.cgi?id=513820](https://bugzilla.gnome.org/show_bug.cgi?id=513820)> Every so often, NetworkManager will scan wireless interfaces for new networks. 
This is good behavior.  However, occasionally users have latency-sensitive
tasks, like online videogames.  It would be nice if it was possible to
temporarily disable scanning without killing NetworkManager and manually
configuring interfaces.I'd probably replace NM with Wicd or, if this is a stay-at-home computer, remove NM entirely and configure /etc/network/interfaces.

I'll be happy to help in any case.

---

### Post by cocuana on 2012-05-21
Hi,

I've exactly the same problem with this card, and I've followed this link, [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) , and installed a new version of the driver following the instructions on readme.txt file.

Now everything goes smooth, steady and fast:)

Regards,

Zé

---

