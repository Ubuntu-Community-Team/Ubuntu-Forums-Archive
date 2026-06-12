---
title: "Samsung N140 wireless issue with Realtek 8192e"
date: 2011-10-19
forum: Networking &amp; Wireless
---

### Post by angus_young on 2011-10-19
Hey Everyone,

I am starting to pull my hair out, i've  been able to to get the Realtek wireless card to work fine in the last 2 version of ubuntu, with either using the samsung-wireless or ndiswrapper techniques

But I'm having problems with wireless either at boot up from cold, or coming out of standby.

Can any shed some light, cheers

Here's output info for information, thanks again




> Samsung N140 Netbook

lspci

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8192E/RTL8192SE Wireless LAN Controller (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

> lspci -nn | grep RTL8192E
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192E/RTL8192SE Wireless LAN Controller [10ec:8192] (rev 01)

ifconfig

eth0      Link encap:Ethernet  HWaddr 00:24:54:3b:73:43  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:26:b6:82:8d:23  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::226:b6ff:fe82:8d23/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:67045 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43457 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:98451023 (98.4 MB)  TX bytes:3137759 (3.1 MB)
          Interrupt:16 Memory:f0100000-f0104000 

> iwconfig

wlan0     IEEE 802.11g  ESSID:"SKY47432"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:24:B2:F4:30:AE   
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:65/100  Signal level:-54 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

> lsmod

Module                  Size  Used by
i915                  505108  2 
drm_kms_helper         32889  1 i915
drm                   192226  3 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
bnep                   17923  2 
parport_pc             32114  0 
vesafb                 13489  0 
ppdev                  12849  0 
rfcomm                 38408  8 
joydev                 17393  0 
acpi_cpufreq           13203  1 
samsung_backlight      13487  0 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
btusb                  18160  2 
psmouse                73673  0 
bluetooth             148839  23 bnep,rfcomm,btusb
serio_raw              12990  0 
binfmt_misc            17292  1 
snd_hda_codec_realtek   254125  1 
nls_iso8859_1          12617  1 
snd_hda_intel          24262  4 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
nls_cp437              12751  1 
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_intel,snd_hda_codec
vfat                   17308  1 
fat                    55577  1 vfat
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
video                  18908  1 i915
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
ndiswrapper           193669  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  43104  0

lsmod | grep ndiswrapper
ndiswrapper           193669  0 


> dmesg

[    0.236442] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.237031] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.237231] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.237480] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.238217]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.238231]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.238238] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.250508] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.250699] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.250882] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    0.251079] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    0.251263] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.251445] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.251629] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    0.251809] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    0.252233] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.252264] vgaarb: loaded
[    0.252270] vgaarb: bridge control possible 0000:00:02.0
[    0.253192] SCSI subsystem initialized
[    0.253396] libata version 3.00 loaded.
[    0.253589] usbcore: registered new interface driver usbfs
[    0.253639] usbcore: registered new interface driver hub
[    0.253758] usbcore: registered new device driver usb
[    0.254172] PCI: Using ACPI for IRQ routing
[    0.267283] PCI: pci_cache_line_size set to 64 bytes
[    0.267440] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.267450] reserve RAM buffer: 000000007f6c0000 - 000000007fffffff 
[    0.267830] NetLabel: Initializing
[    0.267838] NetLabel:  domain hash size = 128
[    0.267843] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.267886] NetLabel:  unlabeled traffic allowed by default
[    0.268115] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.268130] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.268146] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.272435] Switching to clocksource hpet
[    0.274510] Switched to NOHz mode on CPU #0
[    0.274681] Switched to NOHz mode on CPU #1
[    0.293793] AppArmor: AppArmor Filesystem Enabled
[    0.293878] pnp: PnP ACPI init
[    0.293925] ACPI: bus type pnp registered
[    0.295097] pnp 00:00: [bus 00-ff]
[    0.295108] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.295117] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.295125] pnp 00:00: [io  0x0d00-0xffff window]
[    0.295134] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.295143] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.295152] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.295161] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.295169] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.295178] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.295187] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.295195] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.295204] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.295213] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.295221] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.295230] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.295239] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.295247] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.295256] pnp 00:00: [mem 0x80000000-0xfebfffff window]
[    0.295265] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    0.295467] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.295581] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    0.295591] pnp 00:01: [mem 0xfed14000-0xfed17fff]
[    0.295599] pnp 00:01: [mem 0xfed18000-0xfed18fff]
[    0.295607] pnp 00:01: [mem 0xfed19000-0xfed19fff]
[    0.295615] pnp 00:01: [mem 0xfed1c000-0xfed1ffff]
[    0.295623] pnp 00:01: [mem 0xfed20000-0xfed3ffff]
[    0.295632] pnp 00:01: [mem 0xfed40000-0xfed44fff]
[    0.295640] pnp 00:01: [mem 0xfed45000-0xfed8ffff]
[    0.295795] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.295817] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.295828] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.295838] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.295848] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.295859] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.295869] system 00:01: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.295879] system 00:01: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.295892] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.297204] pnp 00:02: [io  0x0000-0x001f]
[    0.297214] pnp 00:02: [io  0x0081-0x0091]
[    0.297222] pnp 00:02: [io  0x0093-0x009f]
[    0.297230] pnp 00:02: [io  0x00c0-0x00df]
[    0.297239] pnp 00:02: [dma 4]
[    0.297398] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.297440] pnp 00:03: [mem 0xff000000-0xffffffff]
[    0.297605] pnp 00:03: Plug and Play ACPI device, IDs INT0800 (active)
[    0.297882] pnp 00:04: [mem 0xfed00000-0xfed003ff]
[    0.298079] system 00:04: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.298093] system 00:04: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.298140] pnp 00:05: [io  0x00f0]
[    0.298165] pnp 00:05: [irq 13]
[    0.298298] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.298343] pnp 00:06: [io  0x0061]
[    0.298351] pnp 00:06: [io  0x0063]
[    0.298359] pnp 00:06: [io  0x0065]
[    0.298366] pnp 00:06: [io  0x0067]
[    0.298374] pnp 00:06: [io  0x0070]
[    0.298381] pnp 00:06: [io  0x0080]
[    0.298388] pnp 00:06: [io  0x0092]
[    0.298396] pnp 00:06: [io  0x00b2-0x00b3]
[    0.298404] pnp 00:06: [io  0x0680-0x069f]
[    0.298411] pnp 00:06: [io  0x0800-0x080f]
[    0.298420] pnp 00:06: [io  0x1000-0x107f]
[    0.298428] pnp 00:06: [io  0x1180-0x11bf]
[    0.298436] pnp 00:06: [io  0x1640-0x164f]
[    0.298655] system 00:06: [io  0x0680-0x069f] has been reserved
[    0.298666] system 00:06: [io  0x0800-0x080f] has been reserved
[    0.298677] system 00:06: [io  0x1000-0x107f] has been reserved
[    0.298687] system 00:06: [io  0x1180-0x11bf] has been reserved
[    0.298697] system 00:06: [io  0x1640-0x164f] has been reserved
[    0.298709] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.298829] pnp 00:07: [io  0x06a0-0x06af]
[    0.298838] pnp 00:07: [io  0x06b0-0x06ff]
[    0.299040] system 00:07: [io  0x06a0-0x06af] has been reserved
[    0.299051] system 00:07: [io  0x06b0-0x06ff] has been reserved
[    0.299063] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.299101] pnp 00:08: [io  0x0070-0x0077]
[    0.299123] pnp 00:08: [irq 8]
[    0.299261] pnp 00:08: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.299371] pnp 00:09: [io  0x0060]
[    0.299380] pnp 00:09: [io  0x0064]
[    0.299399] pnp 00:09: [irq 1]
[    0.299545] pnp 00:09: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.299590] pnp 00:0a: [irq 12]
[    0.299727] pnp 00:0a: Plug and Play ACPI device, IDs PNP0f13 (active)
[    0.300204] pnp: PnP ACPI: found 11 devices
[    0.300213] ACPI: ACPI bus type pnp unregistered
[    0.300224] PnPBIOS: Disabled by ACPI PNP
[    0.341424] PCI: max bus depth: 1 pci_try_num: 2
[    0.341502] pci 0000:00:1c.2: BAR 14: assigned [mem 0x80000000-0x800fffff]
[    0.341520] pci 0000:00:1c.0: BAR 15: assigned [mem 0x80400000-0x805fffff 64bit pref]
[    0.341532] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.341545] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.341560] pci 0000:00:1c.0:   bridge window [mem 0xf0100000-0xf01fffff]
[    0.341574] pci 0000:00:1c.0:   bridge window [mem 0x80400000-0x805fffff 64bit pref]
[    0.341595] pci 0000:03:00.0: BAR 6: assigned [mem 0xf0520000-0xf053ffff pref]
[    0.341605] pci 0000:00:1c.2: PCI bridge to [bus 03-03]
[    0.341615] pci 0000:00:1c.2:   bridge window [io  0x3000-0x3fff]
[    0.341629] pci 0000:00:1c.2:   bridge window [mem 0x80000000-0x803fffff]
[    0.341642] pci 0000:00:1c.2:   bridge window [mem 0xf0500000-0xf05fffff 64bit pref]
[    0.341659] pci 0000:00:1e.0: PCI bridge to [bus 04-04]
[    0.341666] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.341678] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.341689] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.341748] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.341763] pci 0000:00:1c.0: setting latency timer to 64
[    0.341794] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.341806] pci 0000:00:1c.2: setting latency timer to 64
[    0.341825] pci 0000:00:1e.0: setting latency timer to 64
[    0.341837] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.341846] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.341855] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.341864] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.341873] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.341882] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.341891] pci_bus 0000:00: resource 10 [mem 0x80000000-0xfebfffff]
[    0.341901] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    0.341909] pci_bus 0000:02: resource 1 [mem 0xf0100000-0xf01fffff]
[    0.341919] pci_bus 0000:02: resource 2 [mem 0x80400000-0x805fffff 64bit pref]
[    0.341929] pci_bus 0000:03: resource 0 [io  0x3000-0x3fff]
[    0.341937] pci_bus 0000:03: resource 1 [mem 0x80000000-0x803fffff]
[    0.341947] pci_bus 0000:03: resource 2 [mem 0xf0500000-0xf05fffff 64bit pref]
[    0.341957] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    0.341966] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    0.341974] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    0.341983] pci_bus 0000:04: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.341992] pci_bus 0000:04: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.342001] pci_bus 0000:04: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.342011] pci_bus 0000:04: resource 10 [mem 0x80000000-0xfebfffff]
[    0.342137] NET: Registered protocol family 2
[    0.342335] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.343232] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.344447] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.345048] TCP: Hash tables configured (established 131072 bind 65536)
[    0.345061] TCP reno registered
[    0.345080] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.345113] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.345437] NET: Registered protocol family 1
[    0.345489] pci 0000:00:02.0: Boot video device
[    0.345683] PCI: CLS 64 bytes, default 64
[    0.345697] Simple Boot Flag at 0x36 set to 0x1
[    0.346768] audit: initializing netlink socket (disabled)
[    0.346797] type=2000 audit(1319060827.344:1): initialized
[    0.409759] highmem bounce pool size: 64 pages
[    0.409778] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.416843] VFS: Disk quotas dquot_6.5.2
[    0.417085] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.419754] fuse init (API version 7.16)
[    0.420230] msgmni has been set to 1679
[    0.421586] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.421710] io scheduler noop registered
[    0.421718] io scheduler deadline registered
[    0.421782] io scheduler cfq registered (default)
[    0.422149] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.422249] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.422432] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.422527] pcieport 0000:00:1c.2: irq 41 for MSI/MSI-X
[    0.422803] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.422910] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.423123] intel_idle: MWAIT substates: 0x20220
[    0.423142] intel_idle: v0.4 model 0x1C
[    0.423148] intel_idle: lapic_timer_reliable_states 0x2
[    0.423169] Marking TSC unstable due to TSC halts in idle states deeper than C2
[    0.423636] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.424134] ACPI: AC Adapter [ADP1] (on-line)
[    0.424416] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.424910] ACPI: Lid Switch [LID0]
[    0.425230] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.425248] ACPI: Power Button [PWRB]
[    0.425403] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.425419] ACPI: Sleep Button [SLPB]
[    0.425588] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.425601] ACPI: Power Button [PWRF]
[    0.425849] ACPI: Fan [FAN0] (off)
[    0.425883] ACPI: acpi_idle yielding to intel_idle
[    0.431490] thermal LNXTHERM:00: registered as thermal_zone0
[    0.431500] ACPI: Thermal Zone [TZ00] (50 C)
[    0.431606] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.431703] ERST: Table is not found!
[    0.431913] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.433132] isapnp: Scanning for PnP cards...
[    0.465395] ACPI: Battery Slot [BAT1] (battery present)
[    0.787854] isapnp: No Plug & Play device found
[    0.934951] Freeing initrd memory: 13300k freed
[    0.959396] Linux agpgart interface v0.103
[    0.959555] agpgart-intel 0000:00:00.0: Intel 945GME Chipset
[    0.959742] agpgart-intel 0000:00:00.0: detected gtt size: 262144K total, 262144K mappable
[    0.959930] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    0.960196] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    0.963385] brd: module loaded
[    0.965012] loop: module loaded
[    0.965372] ata_piix 0000:00:1f.2: version 2.13
[    0.965427] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.965440] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    1.120069] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.120808] scsi0 : ata_piix
[    1.121065] scsi1 : ata_piix
[    1.122555] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    1.122563] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    1.122679] ata2: port disabled. ignoring.
[    1.123685] Fixed MDIO Bus: probed
[    1.123759] PPP generic driver version 2.4.2
[    1.123905] tun: Universal TUN/TAP device driver, 1.6
[    1.123910] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.124175] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.124244] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.124280] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.124289] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.124396] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.124439] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    1.124459] ehci_hcd 0000:00:1d.7: debug port 1
[    1.128350] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    1.128391] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf0444000
[    1.144036] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.144349] hub 1-0:1.0: USB hub found
[    1.144361] hub 1-0:1.0: 8 ports detected
[    1.144530] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.144568] uhci_hcd: USB Universal Host Controller Interface driver
[    1.144646] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.144663] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.144671] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.144772] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.144817] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[    1.145128] hub 2-0:1.0: USB hub found
[    1.145140] hub 2-0:1.0: 2 ports detected
[    1.145278] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.145293] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.145301] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.145408] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.145475] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    1.145779] hub 3-0:1.0: USB hub found
[    1.145799] hub 3-0:1.0: 2 ports detected
[    1.145954] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 20 (level, low) -> IRQ 20
[    1.145969] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.145977] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.146077] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.146140] uhci_hcd 0000:00:1d.2: irq 20, io base 0x00001860
[    1.146463] hub 4-0:1.0: USB hub found
[    1.146475] hub 4-0:1.0: 2 ports detected
[    1.146616] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    1.146632] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.146640] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.146738] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.146797] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[    1.147097] hub 5-0:1.0: USB hub found
[    1.147108] hub 5-0:1.0: 2 ports detected
[    1.147368] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.150460] i8042: Detected active multiplexing controller, rev 1.1
[    1.152038] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.152060] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.152151] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.152221] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.152289] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.152612] mousedev: PS/2 mouse device common for all mice
[    1.153078] rtc_cmos 00:08: RTC can wake from S4
[    1.153275] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    1.153322] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.153588] device-mapper: uevent: version 1.0.3
[    1.153818] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: [email]dm-devel@redhat.com[/email]
[    1.153902] EISA: Probing bus 0 at eisa.0
[    1.153909] EISA: Cannot allocate resource for mainboard
[    1.153916] Cannot allocate resource for EISA slot 1
[    1.153922] Cannot allocate resource for EISA slot 2
[    1.153927] Cannot allocate resource for EISA slot 3
[    1.153933] Cannot allocate resource for EISA slot 4
[    1.153939] Cannot allocate resource for EISA slot 5
[    1.153944] Cannot allocate resource for EISA slot 6
[    1.153950] Cannot allocate resource for EISA slot 7
[    1.153955] Cannot allocate resource for EISA slot 8
[    1.153960] EISA: Detected 0 cards.
[    1.153980] cpufreq-nforce2: No nForce2 chipset.
[    1.154145] cpuidle: using governor ladder
[    1.154425] cpuidle: using governor menu
[    1.154431] EFI Variables Facility v0.08 2004-May-17
[    1.155098] TCP cubic registered
[    1.155478] NET: Registered protocol family 10
[    1.156929] NET: Registered protocol family 17
[    1.156982] Registering the dns_resolver key type
[    1.157029] Using IPI No-Shortcut mode
[    1.157284] PM: Hibernation image not present or could not be loaded.
[    1.157310] registered taskstats version 1
[    1.174995]   Magic number: 15:915:803
[    1.175162] rtc_cmos 00:08: setting system clock to 2011-10-19 21:47:09 UTC (1319060829)
[    1.175188] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.175193] EDD information not available.
[    1.193210] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.333532] ata1.00: ATA-8: ST9250315AS, 0001SDM1, max UDMA/133
[    1.333550] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.348886] ata1.00: configured for UDMA/133
[    1.349359] scsi 0:0:0:0: Direct-Access     ATA      ST9250315AS      0001 PQ: 0 ANSI: 5
[    1.349710] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.349814] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.349966] sd 0:0:0:0: [sda] Write Protect is off
[    1.349977] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.350095] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.382954]  sda: sda1 sda2 < sda5 > sda3
[    1.383986] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.384098] Freeing unused kernel memory: 696k freed
[    1.384702] Write protecting the kernel text: 5328k
[    1.384801] Write protecting the kernel read-only data: 2188k
[    1.429044] udevd[83]: starting version 173
[    1.568105] usb 1-8: new high speed USB device number 3 using ehci_hcd
[    1.651395] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.651453] r8169 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.651530] r8169 0000:03:00.0: setting latency timer to 64
[    1.651635] r8169 0000:03:00.0: irq 42 for MSI/MSI-X
[    1.678276] r8169 0000:03:00.0: eth0: RTL8102e at 0xf801c000, 00:24:54:3b:73:43, XID 04c00000 IRQ 42
[    1.956081] usb 4-2: new full speed USB device number 2 using uhci_hcd
[    2.138380] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   11.528645] udevd[306]: starting version 173
[   11.591650] Adding 8848380k swap on /dev/sda5.  Priority:-1 extents:1 across:8848380k 
[   11.604243] lp: driver loaded but no devices found
[   11.646550] Disabling lock debugging due to kernel taint
[   11.668704] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[   11.928647] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   12.006478] ndiswrapper: driver net819xp (Realtek Semiconductor Corp.,03/07/2010,1680.4.0307.2010) loaded
[   12.007060] ndiswrapper 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.008299] ndiswrapper 0000:02:00.0: setting latency timer to 64
[   12.127251] ndiswrapper: using IRQ 16
[   12.192996] acpi device:04: registered as cooling_device3
[   12.199670] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5
[   12.199861] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   12.426495] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   12.426614] HDA Intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[   12.426683] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   12.529530] hda_codec: ALC269: BIOS auto-probing.
[   12.644993] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   12.645323] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   12.651283] type=1400 audit(1319060840.970:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=603 comm="apparmor_parser"
[   12.677579] type=1400 audit(1319060840.998:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=603 comm="apparmor_parser"
[   12.678609] type=1400 audit(1319060840.998:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=603 comm="apparmor_parser"
[   12.746033] wlan0: ethernet device 00:26:b6:82:8d:23 using NDIS driver: net819xp, version: 0x500a5, NDIS version: 0x500, vendor: 'Realtek RTL8190 Wireless LAN (Mini-)PCI NIC                                     ', 10EC:8192.5.conf
[   12.746101] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   12.786567] intel_rng: FWH not detected
[   12.824525] leds_ss4200: no LED devices found
[   12.874684] usbcore: registered new interface driver ndiswrapper
[   13.037697] Bluetooth: Core ver 2.16
[   13.047439] NET: Registered protocol family 31
[   13.047448] Bluetooth: HCI device and connection manager initialized
[   13.047457] Bluetooth: HCI socket layer initialized
[   13.047464] Bluetooth: L2CAP socket layer initialized
[   13.057626] Bluetooth: SCO socket layer initialized
[   13.065958] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   13.076818] usbcore: registered new interface driver btusb
[   13.126758] Linux video capture interface: v2.00
[   13.134580] uvcvideo: Found UVC 1.00 device WebCam SCB-0340N (0ac8:c33f)
[   13.149278] input: WebCam SCB-0340N as /devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/input/input8
[   13.153600] usbcore: registered new interface driver uvcvideo
[   13.153612] USB Video Class driver (v1.1.0)
[   13.188808] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.213339] r8169 0000:03:00.0: eth0: link down
[   13.213971] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.451187] type=1400 audit(1319060841.770:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=741 comm="apparmor_parser"
[   13.454802] type=1400 audit(1319060841.774:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=742 comm="apparmor_parser"
[   13.457614] type=1400 audit(1319060841.778:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=742 comm="apparmor_parser"
[   13.458646] type=1400 audit(1319060841.778:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=742 comm="apparmor_parser"
[   13.479994] type=1400 audit(1319060841.798:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=746 comm="apparmor_parser"
[   13.497787] type=1400 audit(1319060841.818:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=746 comm="apparmor_parser"
[   13.506423] type=1400 audit(1319060841.826:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=744 comm="apparmor_parser"
[   13.856356] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04773/0xa40000/0xa0000
[   13.898382] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
[   14.054361] init: failsafe main process (794) killed by TERM signal
[   14.060682] init: apport pre-start process (812) terminated with status 1
[   14.122404] init: apport post-stop process (848) terminated with status 1
[   15.158672] Bluetooth: RFCOMM TTY layer initialized
[   15.158691] Bluetooth: RFCOMM socket layer initialized
[   15.158699] Bluetooth: RFCOMM ver 1.11
[   15.203974] vesafb: mode is 800x600x32, linelength=3200, pages=0
[   15.203984] vesafb: scrolling: redraw
[   15.203994] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   15.205065] vesafb: framebuffer at 0xd0000000, mapped to 0xf9200000, using 1920k, total 1920k
[   15.205546] Console: switching to colour frame buffer device 100x37
[   15.205618] fb0: VESA VGA frame buffer device
[   15.218540] ppdev: user-space parallel port driver
[   15.460863] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.460874] Bluetooth: BNEP filters: protocol multicast
[   15.750547] [drm] Initialized drm 1.1.0 20060810
[   15.779447] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.779464] i915 0000:00:02.0: setting latency timer to 64
[   15.832612] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   15.832623] [drm] Driver supports precise vblank timestamp query.
[   15.868003] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   16.163618] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   16.180672] [drm] initialized overlay support
[   16.208224] checking generic (d0000000 1e0000) vs hw (d0000000 10000000)
[   16.208247] fb: conflicting fb hw usage inteldrmfb vs VESA VGA - removing generic driver
[   16.208463] Console: switching to colour dummy device 80x25
[   16.208956] fbcon: inteldrmfb (fb0) is primary device
[   16.209248] Console: switching to colour frame buffer device 128x37
[   16.209275] fb0: inteldrmfb frame buffer device
[   16.209281] drm: registered panic notifier
[   16.209366] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   19.325533] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   24.849600] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[   25.198997] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   35.984092] wlan0: no IPv6 routers present
[   53.232089] wlan0: no IPv6 routers present
[  124.509150] exe (1912): /proc/1912/oom_adj is deprecated, please use /proc/1912/oom_score_adj instead.


> sudo lshw -C network
[sudo] password for delboy: 
  *-network               
       description: Wireless interface
       product: RTL8192E/RTL8192SE Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:26:b6:82:8d:23
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net819xp driverversion=1.56+Realtek Semiconductor Corp. ip=192.168.0.4 latency=0 link=yes multicast=yes wireless=IEEE 802.11g
       resources: irq:16 ioport:2000(size=256) memory:f0100000-f0103fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:24:54:3b:73:43
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:3000(size=256) memory:f0510000-f0510fff memory:f0500000-f050ffff memory:f0520000-f053ffff

uname -mr
3.0.0-12-generic i686

---

### Post by angus_young on 2011-10-20
Sorry for the bump

But any ideas?

---

