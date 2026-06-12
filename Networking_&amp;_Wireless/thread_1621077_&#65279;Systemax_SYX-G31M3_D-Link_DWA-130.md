---
title: "&#65279;Systemax SYX-G31M3 D-Link DWA-130"
date: 2010-11-13
forum: Networking &amp; Wireless
---

### Post by sks24 on 2010-11-13
I can't connect to my wireless network ("tuan") with this particular computer (my others will connect).  The CAT5 connection does fine.

I think that all I need to do is enable wireless networking, but I've approached it several different ways and I just can't bring this home.  

I did try ```
sudo ifconfig wlan1 up
``` and the Network Tools showed the wireless interface (wlan1) as active and enabled, but no pages load if I disconnect the ethernet cable.  
 
It would also be nice, upon solving this problem, if the "Wireless Network Connection" icon would appear in my system tray.  
 
Thanks in advance for all your help.  My apologies if I've left out information which you need to to assist me.   
 
Best,
Scott
 
Machine Brand/Model:
Systemax SYX-G31M3
 
```
lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 07d1:3300 D-Link System 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
 
Despite trying everything I could think of for 'wireless device' (and also using 'lsusb') I could only get "command not found" &
"System: No such file or directory" for "$ lspci -nn | grep 'Wireless Brand'
 
$ ifconfig
 
```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:21:30:aa:84  
         inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
         inet6 addr: fe80::224:21ff:fe30:aa84/64 Scope:Link
         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
         RX packets:4139 errors:0 dropped:0 overruns:0 frame:0
         TX packets:3142 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000 
         RX bytes:5263070 (5.2 MB)  TX bytes:371944 (371.9 KB)
         Interrupt:26 Base address:0x4000 
 
lo        Link encap:Local Loopback  
         inet addr:127.0.0.1  Mask:255.0.0.0
         inet6 addr: ::1/128 Scope:Host
         UP LOOPBACK RUNNING  MTU:16436  Metric:1
         RX packets:16 errors:0 dropped:0 overruns:0 frame:0
         TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:0 
         RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)
```
 
iwconfig:
```
lo        no wireless extensions.
 
eth0      no wireless extensions.
 
wlan1     IEEE 802.11g  ESSID:off/any  
         Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
         Bit Rate:65 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
         RTS thr:off   Fragment thr:off
         Encryption key:off
         Power Management:off
         Link Quality:0  Signal level:0  Noise level:0
         Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
         Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
 
```
sudo lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
snd_hda_codec_realtek   203375  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_intel          22037  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  286079  2 
lp                      7060  0 
ppdev                   5259  0 
ndiswrapper           184677  0 
psmouse                63245  0 
drm_kms_helper         29297  1 i915
snd                    54180  17 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             25962  1 
parport                32635  3 lp,ppdev,parport_pc
serio_raw               3978  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
drm                   162409  3 i915,drm_kms_helper
intel_agp              24119  2 i915
agpgart                31724  2 drm,intel_agp
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
output                  1871  1 video
r8169                  34076  0 
mii                     4381  1 r8169
```
 
 
dmesg:
 
```
[    0.004213] CPU: Processor Core ID: 0
[    0.004217] mce: CPU supports 6 MCE banks
[    0.004225] CPU0: Thermal monitoring enabled (TM2)
[    0.004229] using mwait in idle threads.
[    0.004235] Performance Events: Core2 events, Intel PMU driver.
[    0.004243] ... version:                2
[    0.004244] ... bit width:              40
[    0.004246] ... generic registers:      2
[    0.004248] ... value mask:             000000ffffffffff
[    0.004249] ... max period:             000000007fffffff
[    0.004251] ... fixed-purpose events:   3
[    0.004253] ... event mask:             0000000700000003
[    0.004256] Checking 'hlt' instruction... OK.
[    0.022426] ACPI: Core revision 20090903
[    0.030554] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.030559] ftrace: allocating 21789 entries in 43 pages
[    0.032055] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.032362] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.075225] CPU0: Intel(R) Pentium(R) Dual  CPU  E2220  @ 2.40GHz stepping 0d
[    0.076001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.008000] Initializing CPU#1
[    0.008000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.008000] CPU: L2 cache: 1024K
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 1
[    0.008000] CPU1: Thermal monitoring enabled (TM2)
[    0.160118] CPU1: Intel(R) Pentium(R) Dual  CPU  E2220  @ 2.40GHz stepping 0d
[    0.160128] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.164017] Brought up 2 CPUs
[    0.164020] Total of 2 processors activated (9679.99 BogoMIPS).
[    0.164345] CPU0 attaching sched-domain:
[    0.164348]  domain 0: span 0-1 level MC
[    0.164350]   groups: 0 1
[    0.164356] CPU1 attaching sched-domain:
[    0.164358]  domain 0: span 0-1 level MC
[    0.164360]   groups: 1 0
[    0.164448] devtmpfs: initialized
[    0.164448] regulator: core version 0.5
[    0.164448] Time: 16:43:54  Date: 11/13/10
[    0.164448] NET: Registered protocol family 16
[    0.164448] Trying to unpack rootfs image as initramfs...
[    0.164448] EISA bus registered
[    0.164448] ACPI: bus type pci registered
[    0.164448] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.164448] PCI: Not using MMCONFIG.
[    0.164448] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=3
[    0.164448] PCI: Using configuration type 1 for base access
[    0.165332] bio: create slab <bio-0> at 0
[    0.166150] ACPI: EC: Look up EC in DSDT
[    0.170192] ACPI: Executed 1 blocks of module-level executable AML code
[    0.174240] ACPI: Interpreter enabled
[    0.174248] ACPI: (supports S0 S3 S4 S5)
[    0.174270] ACPI: Using IOAPIC for interrupt routing
[    0.174323] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.177962] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.177965] PCI: Using MMCONFIG for extended config space
[    0.185328] ACPI Warning: Incorrect checksum in table [OEMB] - C2, should be BB (20090903/tbutils-314)
[    0.186132] ACPI: No dock devices found.
[    0.186415] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.186506] pci 0000:00:02.0: reg 10 32bit mmio: [0xfea80000-0xfeafffff]
[    0.186511] pci 0000:00:02.0: reg 14 io port: [0xdc00-0xdc07]
[    0.186515] pci 0000:00:02.0: reg 18 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.186520] pci 0000:00:02.0: reg 1c 32bit mmio: [0xfe900000-0xfe9fffff]
[    0.186599] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfea78000-0xfea7bfff]
[    0.186640] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.186644] pci 0000:00:1b.0: PME# disabled
[    0.186705] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.186709] pci 0000:00:1c.0: PME# disabled
[    0.186772] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.186775] pci 0000:00:1c.1: PME# disabled
[    0.186823] pci 0000:00:1d.0: reg 20 io port: [0xd880-0xd89f]
[    0.186870] pci 0000:00:1d.1: reg 20 io port: [0xd800-0xd81f]
[    0.186919] pci 0000:00:1d.2: reg 20 io port: [0xd480-0xd49f]
[    0.186966] pci 0000:00:1d.3: reg 20 io port: [0xd400-0xd41f]
[    0.187018] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfea77c00-0xfea77fff]
[    0.187067] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.187072] pci 0000:00:1d.7: PME# disabled
[    0.187197] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.187203] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.187207] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.187211] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0a00 (mask 00ff)
[    0.187214] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0a00 (mask 0017)
[    0.187217] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 4700 (mask 00ff)
[    0.187256] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.187262] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.187269] pci 0000:00:1f.1: reg 18 io port: [0x8f0-0x8f7]
[    0.187275] pci 0000:00:1f.1: reg 1c io port: [0x8f8-0x8fb]
[    0.187281] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]
[    0.187323] pci 0000:00:1f.2: reg 10 io port: [0xd080-0xd087]
[    0.187329] pci 0000:00:1f.2: reg 14 io port: [0xd000-0xd003]
[    0.187334] pci 0000:00:1f.2: reg 18 io port: [0xcc00-0xcc07]
[    0.187340] pci 0000:00:1f.2: reg 1c io port: [0xc880-0xc883]
[    0.187346] pci 0000:00:1f.2: reg 20 io port: [0xc800-0xc80f]
[    0.187368] pci 0000:00:1f.2: PME# supported from D3hot
[    0.187372] pci 0000:00:1f.2: PME# disabled
[    0.187415] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
[    0.187527] pci 0000:02:00.0: reg 10 io port: [0xe800-0xe8ff]
[    0.187547] pci 0000:02:00.0: reg 18 64bit mmio pref: [0xfdfff000-0xfdffffff]
[    0.187561] pci 0000:02:00.0: reg 20 64bit mmio pref: [0xfdfe0000-0xfdfeffff]
[    0.187570] pci 0000:02:00.0: reg 30 32bit mmio pref: [0xfebf0000-0xfebfffff]
[    0.187609] pci 0000:02:00.0: supports D1 D2
[    0.187611] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.187616] pci 0000:02:00.0: PME# disabled
[    0.187673] pci 0000:00:1c.1: bridge io port: [0xe000-0xefff]
[    0.187677] pci 0000:00:1c.1: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
[    0.187683] pci 0000:00:1c.1: bridge 64bit mmio pref: [0xfdf00000-0xfdffffff]
[    0.187731] pci 0000:00:1e.0: transparent bridge
[    0.187752] pci_bus 0000:00: on NUMA node 0
[    0.187758] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.187905] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.188035] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.188093] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    0.196226] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.196329] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.196427] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.196525] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 *6 7 10 11 12 14 15)
[    0.196623] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.196721] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.196822] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.196922] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.197027] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.197038] vgaarb: loaded
[    0.197153] SCSI subsystem initialized
[    0.197241] libata version 3.00 loaded.
[    0.197310] usbcore: registered new interface driver usbfs
[    0.197322] usbcore: registered new interface driver hub
[    0.197350] usbcore: registered new device driver usb
[    0.197470] ACPI: WMI: Mapper loaded
[    0.197472] PCI: Using ACPI for IRQ routing
[    0.197610] NetLabel: Initializing
[    0.197612] NetLabel:  domain hash size = 128
[    0.197614] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.197625] NetLabel:  unlabeled traffic allowed by default
[    0.197759] hpet clockevent registered
[    0.197762] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.197766] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.197771] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.200154] Switching to clocksource tsc
[    0.205931] AppArmor: AppArmor Filesystem Enabled
[    0.205948] pnp: PnP ACPI init
[    0.205967] ACPI: bus type pnp registered
[    0.210001] pnp: PnP ACPI: found 18 devices
[    0.210004] ACPI: ACPI bus type pnp unregistered
[    0.210008] PnPBIOS: Disabled by ACPI PNP
[    0.210022] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    0.210031] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    0.210033] system 00:07: ioport range 0x800-0x87f has been reserved
[    0.210036] system 00:07: ioport range 0x480-0x4bf has been reserved
[    0.210038] system 00:07: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.210041] system 00:07: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.210044] system 00:07: iomem range 0xfed45000-0xfed89fff has been reserved
[    0.210050] system 00:09: iomem range 0xffc00000-0xfff7ffff has been reserved
[    0.210055] system 00:0a: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.210057] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.210063] system 00:0d: ioport range 0xa00-0xadf has been reserved
[    0.210066] system 00:0d: ioport range 0xae0-0xaef has been reserved
[    0.210072] system 00:10: iomem range 0xe0000000-0xefffffff has been reserved
[    0.210077] system 00:11: iomem range 0x0-0x9ffff could not be reserved
[    0.210080] system 00:11: iomem range 0xc0000-0xcffff could not be reserved
[    0.210082] system 00:11: iomem range 0xe0000-0xfffff could not be reserved
[    0.210085] system 00:11: iomem range 0x100000-0xbf6fffff could not be reserved
[    0.244783] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    0.244787] pci 0000:00:1c.0:   IO window: 0x1000-0x1fff
[    0.244792] pci 0000:00:1c.0:   MEM window: 0xc0000000-0xc01fffff
[    0.244796] pci 0000:00:1c.0:   PREFETCH window: 0x000000c0200000-0x000000c03fffff
[    0.244802] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
[    0.244805] pci 0000:00:1c.1:   IO window: 0xe000-0xefff
[    0.244810] pci 0000:00:1c.1:   MEM window: 0xfeb00000-0xfebfffff
[    0.244814] pci 0000:00:1c.1:   PREFETCH window: 0x000000fdf00000-0x000000fdffffff
[    0.244820] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.244822] pci 0000:00:1e.0:   IO window: disabled
[    0.244826] pci 0000:00:1e.0:   MEM window: disabled
[    0.244830] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.244843] pci 0000:00:1c.0: enabling device (0104 -> 0107)
[    0.244852]   alloc irq_desc for 16 on node -1
[    0.244854]   alloc kstat_irqs on node -1
[    0.244861] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.244866] pci 0000:00:1c.0: setting latency timer to 64
[    0.244874]   alloc irq_desc for 17 on node -1
[    0.244875]   alloc kstat_irqs on node -1
[    0.244879] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.244883] pci 0000:00:1c.1: setting latency timer to 64
[    0.244890] pci 0000:00:1e.0: setting latency timer to 64
[    0.244894] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.244896] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.244898] pci_bus 0000:01: resource 0 io:  [0x1000-0x1fff]
[    0.244901] pci_bus 0000:01: resource 1 mem: [0xc0000000-0xc01fffff]
[    0.244903] pci_bus 0000:01: resource 2 pref mem [0xc0200000-0xc03fffff]
[    0.244905] pci_bus 0000:02: resource 0 io:  [0xe000-0xefff]
[    0.244907] pci_bus 0000:02: resource 1 mem: [0xfeb00000-0xfebfffff]
[    0.244910] pci_bus 0000:02: resource 2 pref mem [0xfdf00000-0xfdffffff]
[    0.244912] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.244914] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
[    0.244951] NET: Registered protocol family 2
[    0.245054] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.245349] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.245831] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.246134] TCP: Hash tables configured (established 131072 bind 65536)
[    0.246137] TCP reno registered
[    0.246245] NET: Registered protocol family 1
[    0.246270] pci 0000:00:02.0: Boot video device
[    0.246531] cpufreq-nforce2: No nForce2 chipset.
[    0.246557] Scanning for low memory corruption every 60 seconds
[    0.246671] audit: initializing netlink socket (disabled)
[    0.246681] type=2000 audit(1289666633.243:1): initialized
[    0.255073] highmem bounce pool size: 64 pages
[    0.255078] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.256455] VFS: Disk quotas dquot_6.5.2
[    0.256517] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.257040] fuse init (API version 7.13)
[    0.257115] msgmni has been set to 1664
[    0.257323] alg: No test for stdrng (krng)
[    0.257377] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.257380] io scheduler noop registered
[    0.257382] io scheduler anticipatory registered
[    0.257384] io scheduler deadline registered
[    0.257416] io scheduler cfq registered (default)
[    0.257548]   alloc irq_desc for 24 on node -1
[    0.257550]   alloc kstat_irqs on node -1
[    0.257561] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.257570] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.257683]   alloc irq_desc for 25 on node -1
[    0.257685]   alloc kstat_irqs on node -1
[    0.257691] pcieport 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.257699] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.257773] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.257790] Firmware did not grant requested _OSC control
[    0.257808] Firmware did not grant requested _OSC control
[    0.257833] Firmware did not grant requested _OSC control
[    0.257844] Firmware did not grant requested _OSC control
[    0.257857] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.257951] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.257954] ACPI: Power Button [PWRB]
[    0.257996] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.257998] ACPI: Power Button [PWRF]
[    0.258612] ACPI: SSDT bf6b00f0 00277 (v01 DpgPmm  P001Ist 00000011 INTL 20051117)
[    0.258901] processor LNXCPU:00: registered as cooling_device0
[    0.259275] ACPI: SSDT bf6b0370 00277 (v01 DpgPmm  P002Ist 00000012 INTL 20051117)
[    0.259545] processor LNXCPU:01: registered as cooling_device1
[    0.263445] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.263540] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.263635] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.263941] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.264188] 00:0e: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.265132] brd: module loaded
[    0.265551] loop: module loaded
[    0.265638] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.265736] ata_piix 0000:00:1f.1: version 2.13
[    0.265754]   alloc irq_desc for 18 on node -1
[    0.265756]   alloc kstat_irqs on node -1
[    0.265763] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.265801] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.265885] scsi0 : ata_piix
[    0.265959] scsi1 : ata_piix
[    0.267127] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.267131] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.267156]   alloc irq_desc for 19 on node -1
[    0.267158]   alloc kstat_irqs on node -1
[    0.267163] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.267167] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.267202] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.267256] scsi2 : ata_piix
[    0.267306] scsi3 : ata_piix
[    0.268477] ata3: SATA max UDMA/133 cmd 0xd080 ctl 0xd000 bmdma 0xc800 irq 19
[    0.268480] ata4: SATA max UDMA/133 cmd 0xcc00 ctl 0xc880 bmdma 0xc808 irq 19
[    0.268558] isapnp: Scanning for PnP cards...
[    0.268784] Fixed MDIO Bus: probed
[    0.268815] PPP generic driver version 2.4.2
[    0.268863] tun: Universal TUN/TAP device driver, 1.6
[    0.268865] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.268947] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.268967]   alloc irq_desc for 23 on node -1
[    0.268969]   alloc kstat_irqs on node -1
[    0.268975] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.268991] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.268994] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.269022] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.269038] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.269048] ehci_hcd 0000:00:1d.7: debug port 1
[    0.272918] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.272954] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfea77c00
[    0.288041] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.288160] usb usb1: configuration #1 chosen from 1 choice
[    0.288190] hub 1-0:1.0: USB hub found
[    0.288199] hub 1-0:1.0: 8 ports detected
[    0.288264] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.288280] uhci_hcd: USB Universal Host Controller Interface driver
[    0.288320] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.288329] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.288332] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.288363] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.288387] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d880
[    0.288465] usb usb2: configuration #1 chosen from 1 choice
[    0.288487] hub 2-0:1.0: USB hub found
[    0.288492] hub 2-0:1.0: 2 ports detected
[    0.288531] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.288536] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.288539] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.288571] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.288592] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d800
[    0.288667] usb usb3: configuration #1 chosen from 1 choice
[    0.288688] hub 3-0:1.0: USB hub found
[    0.288693] hub 3-0:1.0: 2 ports detected
[    0.288729] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.288734] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.288737] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.288768] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.288796] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d480
[    0.288876] usb usb4: configuration #1 chosen from 1 choice
[    0.288898] hub 4-0:1.0: USB hub found
[    0.288903] hub 4-0:1.0: 2 ports detected
[    0.288940] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.288945] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.288948] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.288980] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.289007] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d400
[    0.289079] usb usb5: configuration #1 chosen from 1 choice
[    0.289100] hub 5-0:1.0: USB hub found
[    0.289105] hub 5-0:1.0: 2 ports detected
[    0.289197] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.291569] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.291574] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.291688] mice: PS/2 mouse device common for all mice
[    0.291797] rtc_cmos 00:03: RTC can wake from S4
[    0.291832] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.291854] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.291961] device-mapper: uevent: version 1.0.3
[    0.315389] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.317670] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.342553] Freeing initrd memory: 7780k freed
[    0.346225] device-mapper: multipath: version 1.1.0 loaded
[    0.346229] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.346391] EISA: Probing bus 0 at eisa.0
[    0.346398] Cannot allocate resource for EISA slot 1
[    0.346417] EISA: Detected 0 cards.
[    0.346485] cpuidle: using governor ladder
[    0.346487] cpuidle: using governor menu
[    0.346901] TCP cubic registered
[    0.347033] NET: Registered protocol family 10
[    0.347469] lo: Disabled Privacy Extensions
[    0.347769] NET: Registered protocol family 17
[    0.348342] Using IPI No-Shortcut mode
[    0.348432] PM: Resume from disk failed.
[    0.348444] registered taskstats version 1
[    0.348692]   Magic number: 2:389:742
[    0.348764] rtc_cmos 00:03: setting system clock to 2010-11-13 16:43:54 UTC (1289666634)
[    0.348767] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.348769] EDD information not available.
[    0.456351] ata1.00: ATAPI: ATAPI   DVD A  DH20A4P, 9P59, max UDMA/66
[    0.456373] ata1.00: limited to UDMA/33 due to 40-wire cable
[    0.456624] ata3.00: ATA-7: Hitachi HDT725025VLA380, V5DOA7EA, max UDMA/133
[    0.456626] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.472368] ata3.00: configured for UDMA/133
[    0.488089] ata1.00: configured for UDMA/33
[    0.611906] usb 1-6: new high speed USB device using ehci_hcd and address 2
[    0.621445] isapnp: No Plug & Play device found
[    0.622517] scsi 0:0:0:0: CD-ROM            ATAPI    DVD A  DH20A4P   9P59 PQ: 0 ANSI: 5
[    0.627678] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.627682] Uniform CD-ROM driver Revision: 3.20
[    0.627829] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    0.627886] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    0.628012] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HDT72502 V5DO PQ: 0 ANSI: 5
[    0.628114] sd 2:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    0.628121] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    0.628155] sd 2:0:0:0: [sda] Write Protect is off
[    0.628157] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.628181] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.628292]  sda: sda1 sda2 < sda5 sda6 >
[    0.675443] sd 2:0:0:0: [sda] Attached SCSI disk
[    0.675454] Freeing unused kernel memory: 656k freed
[    0.675753] Write protecting the kernel text: 4684k
[    0.675789] Write protecting the kernel read-only data: 1840k
[    0.691302] udev: starting version 151
[    0.735594] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.735618] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.735659] r8169 0000:02:00.0: setting latency timer to 64
[    0.735703]   alloc irq_desc for 26 on node -1
[    0.735705]   alloc kstat_irqs on node -1
[    0.735721] r8169 0000:02:00.0: irq 26 for MSI/MSI-X
[    0.750554] usb 1-6: configuration #1 chosen from 1 choice
[    0.775765] eth0: RTL8168c/8111c at 0xf8064000, 00:24:21:30:aa:84, XID 1c4000c0 IRQ 26
[    1.114349] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    8.265260] udev: starting version 151
[    8.334004] Adding 3504120k swap on /dev/sda6.  Priority:-1 extents:1 across:3504120k 
[    8.400740] Linux agpgart interface v0.103
[    8.403018] agpgart-intel 0000:00:00.0: Intel G33 Chipset
[    8.403281] agpgart-intel 0000:00:00.0: detected 7164K stolen memory
[    8.431759] intel_rng: FWH not detected
[    8.509765] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    8.525412] [drm] Initialized drm 1.1.0 20060810
[    8.542334] parport_pc 00:0f: reported by Plug and Play ACPI
[    8.542379] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    8.543813] type=1505 audit(1289684642.691:2):  operation="profile_load" pid=574 name="/sbin/dhclient3"
[    8.544990] type=1505 audit(1289684642.695:3):  operation="profile_load" pid=574 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    8.545300] type=1505 audit(1289684642.695:4):  operation="profile_load" pid=574 name="/usr/lib/connman/scripts/dhclient-script"
[    8.560455] Disabling lock debugging due to kernel taint
[    8.576654] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[    8.581576] ppdev: user-space parallel port driver
[    8.591729] lp: driver loaded but no devices found
[    8.593926] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.593933] i915 0000:00:02.0: setting latency timer to 64
[    8.596865] mtrr: type mismatch for d0000000,10000000 old: write-back new: write-combining
[    8.596868] [drm] MTRR allocation failed.  Graphics performance may suffer.
[    8.598491]   alloc irq_desc for 27 on node -1
[    8.598494]   alloc kstat_irqs on node -1
[    8.598503] i915 0000:00:02.0: irq 27 for MSI/MSI-X
[    8.598510] [drm] set up 7M of stolen space
[    8.598913] [drm] initialized overlay support
[    8.636673] lp0: using parport0 (interrupt-driven).
[    8.720921] psmouse serio1: ID: 10 00 64
[    8.761067] fb0: inteldrmfb frame buffer device
[    8.761070] registered panic notifier
[    8.761773] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    8.761826] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.761852] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    8.766191] vga16fb: initializing
[    8.766195] vga16fb: mapped to 0xc00a0000
[    8.766200] vga16fb: not registering due to another framebuffer present
[    8.801336] r8169: eth0: link up
[    8.801340] r8169: eth0: link up
[    8.832744] hda_codec: ALC888: BIOS auto-probing.
[    8.834130] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input4
[    8.877309] Console: switching to colour frame buffer device 160x64
[    9.130036] type=1505 audit(1289684643.279:5):  operation="profile_load" pid=853 name="/usr/share/gdm/guest-session/Xsession"
[    9.136948] type=1505 audit(1289684643.287:6):  operation="profile_replace" pid=854 name="/sbin/dhclient3"
[    9.137519] type=1505 audit(1289684643.287:7):  operation="profile_replace" pid=854 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    9.137835] type=1505 audit(1289684643.287:8):  operation="profile_replace" pid=854 name="/usr/lib/connman/scripts/dhclient-script"
[    9.143285] type=1505 audit(1289684643.291:9):  operation="profile_load" pid=855 name="/usr/bin/evince"
[    9.151127] type=1505 audit(1289684643.299:10):  operation="profile_load" pid=855 name="/usr/bin/evince-previewer"
[    9.156594] type=1505 audit(1289684643.307:11):  operation="profile_load" pid=855 name="/usr/bin/evince-thumbnailer"
[    9.160567] usb 1-6: reset high speed USB device using ehci_hcd and address 2
[    9.296386] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[    9.398853] apm: BIOS not found.
[    9.651869] ndiswrapper: driver net8192su (D-Link Corporation,04/08/2009,5.1071.0408.2009) loaded
[    9.930053] CPU0 attaching NULL sched-domain.
[    9.930060] CPU1 attaching NULL sched-domain.
[    9.952071] CPU0 attaching sched-domain:
[    9.952074]  domain 0: span 0-1 level MC
[    9.952077]   groups: 0 1
[    9.952082] CPU1 attaching sched-domain:
[    9.952084]  domain 0: span 0-1 level MC
[    9.952086]   groups: 1 0
[   11.328781] wlan0: ethernet device 00:24:01:f0:de:d0 using NDIS driver: net8192su, version: 0x1, NDIS version: 0x500, vendor: 'Realtek RTL8192S Wireless LAN USB NIC                                     ', 07D1:3300.F.conf
[   11.328823] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   11.328880] usbcore: registered new interface driver ndiswrapper
[   11.348045] ndiswrapper: changing interface name from 'wlan0' to 'wlan1'
[   11.348102] udev: renamed network interface wlan0 to wlan1
[   11.385616] CPU0 attaching NULL sched-domain.
[   11.385623] CPU1 attaching NULL sched-domain.
[   11.408119] CPU0 attaching sched-domain:
[   11.408125]  domain 0: span 0-1 level MC
[   11.408130]   groups: 0 1
[   11.408139] CPU1 attaching sched-domain:
[   11.408143]  domain 0: span 0-1 level MC
[   11.408147]   groups: 1 0
[   18.808506] eth0: no IPv6 routers present
[   26.324674] lo: Disabled Privacy Extensions
```
 
```
sudo lshw -C network
 *-network               
      description: Ethernet interface
      product: RTL8111/8168B PCI Express Gigabit Ethernet controller
      vendor: Realtek Semiconductor Co., Ltd.
      physical id: 0
      bus info: pci@0000:02:00.0
      logical name: eth0
      version: 02
      serial: 00:24:21:30:aa:84
      size: 100MB/s
      capacity: 1GB/s
      width: 64 bits
      clock: 33MHz
      capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
      configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.2 latency=0 link=yes multicast=yes port=MII speed=100MB/s
      resources: irq:26 ioport:e800(size=256) memory:fdfff000-fdffffff(prefetchable) memory:fdfe0000-fdfeffff(prefetchable) memory:febf0000-febfffff(prefetchable)
 *-network DISABLED
      description: Wireless interface
      physical id: 1
      logical name: wlan1
      serial: 00:24:01:f0:de:d0
      capabilities: ethernet physical wireless
      configuration: broadcast=yes driver=ndiswrapper+net8192su driverversion=1.55+D-Link Corporation,04/08/20 link=no multicast=yes wireless=IEEE 802.11g
jim@dhcppc1:~$ 

```
 
```
sudo iwlist scan
lo        Interface doesn't support scanning.
 
eth0      Interface doesn't support scanning.
 
wlan1     Scan completed :
         Cell 01 - Address: 00:14:BF:00:71:12
                   ESSID:"tuan"
                   Protocol:IEEE 802.11g
                   Mode:Managed
                   Frequency:2.437 GHz (Channel 6)
                   Quality:40/100  Signal level:-70 dBm  Noise level:-96 dBm
                   Encryption key:on
                   Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                             24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                             12 Mb/s; 48 Mb/s
                   Extra:bcn_int=100
                   Extra:atim=0
                   IE: WPA Version 1
                       Group Cipher : TKIP
                       Pairwise Ciphers (1) : TKIP
                       Authentication Suites (1) : PSK
```
 
```
sudo lsb_release -d
Description:        Ubuntu 10.04.1 LTS
```
 
```
sudo uname -mr
2.6.32-25-generic i686
```
 
```
sudo lsb_release -d
Description:        Ubuntu 10.04.1 LTS
jim@dhcppc1:~$ sudo uname -mr
2.6.32-25-generic i686
jim@dhcppc1:~$ sudo /etc/init.d/networking restart
* Reconfiguring network interfaces...                                                     There is already a pid file /var/run/dhclient.eth0.pid with pid 1457
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/
 
Listening on LPF/eth0/00:24:21:30:aa:84
Sending on   LPF/eth0/00:24:21:30:aa:84
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/
 
Listening on LPF/eth0/00:24:21:30:aa:84
Sending on   LPF/eth0/00:24:21:30:aa:84
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPOFFER of 192.168.0.2 from 192.168.0.1
DHCPREQUEST of 192.168.0.2 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.0.2 from 192.168.0.1
bound to 192.168.0.2 -- renewal in 123450 seconds.
```

---

### Post by sks24 on 2010-11-14
Also: if I disconnect the ethernet cable during an Internet session, I cannot reconnect to the Internet by simply reconnecting the cable.  I have to re-start the computer with the cable connected.

---

### Post by sks24 on 2010-11-17
Update:

I finally was able to get the Network Manager to install, but still no wireless network icon in the system tray, and, in any case, I can't use a command-line method to log on to my wireless network.  

I found a new wireless troubleshooting procedure with a "single, new question" [here]("https://help.ubuntu.com/community/WirelessTroubleshootingProcedure").  So maybe this might help. 

I hate to keep bugging you with this, but I just can't seem to wrap this up.  Here's the code:

And, again, thanks for your time and consideration of this matter. 

```
jim@dhcppc1:~$ sudo apt-get update; sudo apt-get install hwinfo grep; sudo lshw -C network; rfkill list; sudo iwlist scanning; cat /etc/network/interfaces; cat /etc/lsb-release; lspci -nn; lsusb; sudo lshw -short; uname -a; dmesg | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|ndiswrapper|NPE|ound|p54|prism|rtl|rt2|rt3|usb|witch|wl';  iwconfig; cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|witch|wl'; sudo hwinfo --netcard ; cat /var/lib/NetworkManager/NetworkManager.state; sudo lsmod
[sudo] password for jim: 
Get:1 http://dl.google.com stable Release.gpg [189B]
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_US
Get:2 http://dl.google.com stable Release [2,544B]    
Get:3 http://dl.google.com stable/main Packages [1,082B]                      
Hit http://archive.ubuntu.com lucid Release.gpg          
Ign http://archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://archive.ubuntu.com lucid-updates Release.gpg
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://archive.ubuntu.com lucid-security Release.gpg
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://archive.ubuntu.com lucid Release
Hit http://archive.ubuntu.com lucid-updates Release
Hit http://archive.ubuntu.com lucid-security Release
Hit http://archive.ubuntu.com lucid/main Packages
Hit http://archive.ubuntu.com lucid/restricted Packages
Hit http://archive.ubuntu.com lucid/restricted Sources
Hit http://archive.ubuntu.com lucid/main Sources
Hit http://archive.ubuntu.com lucid/multiverse Sources
Hit http://archive.ubuntu.com lucid/universe Sources
Hit http://archive.ubuntu.com lucid/universe Packages
Hit http://archive.ubuntu.com lucid/multiverse Packages
Hit http://archive.ubuntu.com lucid-updates/main Packages
Hit http://archive.ubuntu.com lucid-updates/restricted Packages
Hit http://archive.ubuntu.com lucid-updates/restricted Sources
Hit http://archive.ubuntu.com lucid-updates/main Sources
Hit http://archive.ubuntu.com lucid-updates/multiverse Sources
Hit http://archive.ubuntu.com lucid-updates/universe Sources
Hit http://archive.ubuntu.com lucid-updates/universe Packages
Hit http://archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://archive.ubuntu.com lucid-security/main Packages
Hit http://archive.ubuntu.com lucid-security/restricted Packages
Hit http://archive.ubuntu.com lucid-security/restricted Sources
Hit http://archive.ubuntu.com lucid-security/main Sources
Hit http://archive.ubuntu.com lucid-security/multiverse Sources
Hit http://archive.ubuntu.com lucid-security/universe Sources
Hit http://archive.ubuntu.com lucid-security/universe Packages
Hit http://archive.ubuntu.com lucid-security/multiverse Packages
Fetched 3,815B in 1s (3,360B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
grep is already the newest version.
The following extra packages will be installed:
  libhd16
The following NEW packages will be installed:
  hwinfo libhd16
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 744kB of archives.
After this operation, 2,060kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://archive.ubuntu.com/ubuntu/ lucid/universe libhd16 16.0-2 [698kB]
Get:2 http://archive.ubuntu.com/ubuntu/ lucid/universe hwinfo 16.0-2 [46.1kB]
Fetched 744kB in 2s (291kB/s)
Selecting previously deselected package libhd16.
(Reading database ... 178419 files and directories currently installed.)
Unpacking libhd16 (from .../libhd16_16.0-2_i386.deb) ...
Selecting previously deselected package hwinfo.
Unpacking hwinfo (from .../hwinfo_16.0-2_i386.deb) ...
Processing triggers for man-db ...
Setting up libhd16 (16.0-2) ...

Setting up hwinfo (16.0-2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:24:21:30:aa:84
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.105 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:26 ioport:e800(size=256) memory:fdfff000-fdffffff(prefetchable) memory:fdfe0000-fdfeffff(prefetchable) memory:febf0000-febfffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:24:01:f0:de:d0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8192su driverversion=1.55+D-Link Corporation,04/08/20 link=no multicast=yes wireless=IEEE 802.11g
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan1     Scan completed :
          Cell 01 - Address: 00:0F:66:CD:10:70
                    ESSID:"pete"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.417 GHz (Channel 2)
                    Quality:59/100  Signal level:-58 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"
00:00.0 Host bridge [0600]: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller [8086:29c0] (rev 10)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82G33/G31 Express Integrated Graphics Controller [8086:29c2] (rev 10)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge [8086:27b8] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation N10/ICH7 Family SATA IDE Controller [8086:27c0] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 01)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c509 Logitech, Inc. Cordless Keyboard & Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 07d1:3300 D-Link System 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
H/W path               Device      Class       Description
==========================================================
                                   system      Z1-7529
/0                                 bus         Z1-7529
/0/0                               memory      64KiB BIOS
/0/4                               processor   Intel(R) Pentium(R) Dual  CPU  E2
/0/4/5                             memory      64KiB L1 cache
/0/4/6                             memory      1MiB L2 cache
/0/4/0.1                           processor   Logical CPU
/0/4/0.2                           processor   Logical CPU
/0/27                              memory      4GiB System Memory
/0/27/0                            memory      2GiB DIMM SDRAM Synchronous
/0/27/1                            memory      2GiB DIMM SDRAM Synchronous
/0/1                               processor   
/0/1/0.1                           processor   Logical CPU
/0/1/0.2                           processor   Logical CPU
/0/100                             bridge      82G33/G31/P35/P31 Express DRAM Co
/0/100/2                           display     82G33/G31 Express Integrated Grap
/0/100/1b                          multimedia  N10/ICH 7 Family High Definition 
/0/100/1c                          bridge      N10/ICH 7 Family PCI Express Port
/0/100/1c.1                        bridge      N10/ICH 7 Family PCI Express Port
/0/100/1c.1/0          eth0        network     RTL8111/8168B PCI Express Gigabit
/0/100/1d                          bus         N10/ICH7 Family USB UHCI Controll
/0/100/1d.1                        bus         N10/ICH 7 Family USB UHCI Control
/0/100/1d.2                        bus         N10/ICH 7 Family USB UHCI Control
/0/100/1d.3                        bus         N10/ICH 7 Family USB UHCI Control
/0/100/1d.7                        bus         N10/ICH 7 Family USB2 EHCI Contro
/0/100/1e                          bridge      82801 PCI Bridge
/0/100/1f                          bridge      82801GB/GR (ICH7 Family) LPC Inte
/0/100/1f.1            scsi0       storage     82801G (ICH7 Family) IDE Controll
/0/100/1f.1/0.0.0      /dev/cdrom  disk        DVD A  DH20A4P
/0/100/1f.2            scsi2       storage     N10/ICH7 Family SATA IDE Controll
/0/100/1f.2/0.0.0      /dev/sda    disk        250GB Hitachi HDT72502
/0/100/1f.2/0.0.0/1    /dev/sda1   volume      151GiB Windows NTFS volume
/0/100/1f.2/0.0.0/2    /dev/sda2   volume      81GiB Extended partition
/0/100/1f.2/0.0.0/2/5  /dev/sda5   volume      77GiB Linux filesystem partition
/0/100/1f.2/0.0.0/2/6  /dev/sda6   volume      3422MiB Linux swap / Solaris part
/0/100/1f.3                        bus         N10/ICH 7 Family SMBus Controller
/1                     wlan1       network     Wireless interface
Linux dhcppc1 2.6.32-25-generic #45-Ubuntu SMP Sat Oct 16 19:48:22 UTC 2010 i686 GNU/Linux
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.205369] ACPI: No dock devices found.
[    0.216561] usbcore: registered new interface driver usbfs
[    0.216571] usbcore: registered new interface driver hub
[    0.216594] usbcore: registered new device driver usb
[    0.217017] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.220265] Switching to clocksource tsc
[    0.225895] pnp: PnP ACPI: found 16 devices
[    0.282422] Firmware did not grant requested _OSC control
[    0.282437] Firmware did not grant requested _OSC control
[    0.282461] Firmware did not grant requested _OSC control
[    0.282472] Firmware did not grant requested _OSC control
[    0.293600] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.311569] usb usb1: configuration #1 chosen from 1 choice
[    0.311595] hub 1-0:1.0: USB hub found
[    0.311869] usb usb2: configuration #1 chosen from 1 choice
[    0.311890] hub 2-0:1.0: USB hub found
[    0.312070] usb usb3: configuration #1 chosen from 1 choice
[    0.312092] hub 3-0:1.0: USB hub found
[    0.312274] usb usb4: configuration #1 chosen from 1 choice
[    0.312295] hub 4-0:1.0: USB hub found
[    0.312473] usb usb5: configuration #1 chosen from 1 choice
[    0.312496] hub 5-0:1.0: USB hub found
[    0.312591] PNP: No PS/2 controller found. Probing ports directly.
[    0.365020] device-mapper: multipath: version 1.1.0 loaded
[    0.365025] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.367554] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.667734] isapnp: No Plug & Play device found
[    0.703555] usb 1-4: new high speed USB device using ehci_hcd and address 3
[    0.803748] eth0: RTL8168c/8111c at 0xf8064000, 00:24:21:30:aa:84, XID 1c4000c0 IRQ 26
[    0.838029] usb 1-4: configuration #1 chosen from 1 choice
[    1.076637] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    1.246145] usb 3-1: configuration #1 chosen from 1 choice
[    8.717360] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[    8.721881] usbcore: registered new interface driver hiddev
[    8.736197] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input3
[    8.736294] generic-usb 0003:046D:C509.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.1-1/input0
[    8.753034] lp: driver loaded but no devices found
[    8.770330] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.1/input/input4
[    8.770444] generic-usb 0003:046D:C509.0002: input,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-1/input1
[    8.770475] usbcore: registered new interface driver usbhid
[    8.770477] usbhid: v2.6:USB HID core driver
[    8.865081] r8169: eth0: link up
[    8.865088] r8169: eth0: link up
[    9.060915] Console: switching to colour frame buffer device 160x64
[    9.221242] usb 1-4: reset high speed USB device using ehci_hcd and address 3
[    9.402024] apm: BIOS not found.
[    9.412127] ndiswrapper: driver net8192su (D-Link Corporation,04/08/2009,5.1071.0408.2009) loaded
[   11.053265] wlan0: ethernet device 00:24:01:f0:de:d0 using NDIS driver: net8192su, version: 0x1, NDIS version: 0x500, vendor: 'Realtek RTL8192S Wireless LAN USB NIC                                     ', 07D1:3300.F.conf
[   11.053313] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   11.053374] usbcore: registered new interface driver ndiswrapper
[   11.066950] ndiswrapper: changing interface name from 'wlan0' to 'wlan1'
[   11.066998] udev: renamed network interface wlan0 to wlan1
[   11.068613] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   19.508090] eth0: no IPv6 routers present
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate:65 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

# which ath5k cannot recover. To prevent this condition, stop
blacklist ath_pci
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist twl4030_wdt
alias usb:v07D1p3300d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v07D1p3302d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v07D1p3303d*dc*dsc*dp*ic*isc*ip* ndiswrapper
24: PCI 200.0: 0200 Ethernet controller                         
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_10ec_8168
  Unique ID: rBUF.fYIqoAO3k5C
  Parent ID: qTvu.4chw4Z9dkyF
  SysFS ID: /devices/pci0000:00/0000:00:1c.1/0000:02:00.0
  SysFS BusID: 0000:02:00.0
  Hardware Class: network
  Model: "Realtek RTL8111/8168B PCI Express Gigabit Ethernet controller"
  Vendor: pci 0x10ec "Realtek Semiconductor Co., Ltd."
  Device: pci 0x8168 "RTL8111/8168B PCI Express Gigabit Ethernet controller"
  SubVendor: pci 0x1462 "Micro-Star International Co., Ltd."
  SubDevice: pci 0x529c 
  Revision: 0x02
  Driver: "r8169"
  Driver Modules: "r8169"
  Device File: eth0
  I/O Ports: 0xe800-0xe8ff (rw)
  Memory Range: 0xfdfff000-0xfdffffff (rw,prefetchable)
  Memory Range: 0xfdfe0000-0xfdfeffff (rw,prefetchable)
  Memory Range: 0xfebf0000-0xfebfffff (ro,prefetchable,disabled)
  IRQ: 26 (5732 events)
  HW Address: 00:24:21:30:aa:84
  Link detected: yes
  Module Alias: "pci:v000010ECd00008168sv00001462sd0000529Cbc02sc00i00"
  Driver Info #0:
    Driver Status: r8169 is active
    Driver Activation Cmd: "modprobe r8169"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #13 (PCI bridge)

47: USB 00.0: 0282 WLAN controller
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_7d1_3300_00e04c000001_if0
  Unique ID: Uc5H.2MkAFFuQiqA
  Parent ID: k4bc.9T1GDCLyFd9
  SysFS ID: /devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0
  SysFS BusID: 1-4:1.0
  Hardware Class: network
  Model: "D-Link 11n Adapter"
  Hotplug: USB
  Vendor: usb 0x07d1 "D-Link System"
  Device: usb 0x3300 "11n Adapter"
  Revision: "2.00"
  Serial ID: "00e04c000001"
  Driver: "ndiswrapper"
  Driver Modules: "ndiswrapper", "ndiswrapper"
  Device File: wlan1
  Features: WLAN
  Speed: 480 Mbps
  HW Address: 00:24:01:f0:de:d0
  Link detected: no
  WLAN channels: 1 2 3 4 5 6 7 8 9 10 11 12 13 14
  WLAN frequencies: 2.412 2.417 2.422 2.427 2.432 2.437 2.442 2.447 2.452 2.457 2.462 2.467 2.472 2.484
  WLAN bitrates: 0.5
  WLAN encryption modes: WEP40 WEP104 TKIP CCMP
  WLAN authentication modes: open sharedkey wpa-psk wpa-eap
  Module Alias: "usb:v07D1p3300d0200dc00dsc00dp00icFFiscFFipFF"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #42 (Hub)

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
Module                  Size  Used by
joydev                  8708  0 
binfmt_misc             6587  1 
snd_hda_codec_realtek   203375  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_intel          22037  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   5259  0 
i915                  286079  3 
lp                      7060  0 
drm_kms_helper         29297  1 i915
snd                    54180  17 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             25962  1 
usbhid                 36110  0 
ndiswrapper           184677  0 
hid                    67032  1 usbhid
psmouse                63245  0 
serio_raw               3978  0 
drm                   162409  4 i915,drm_kms_helper
soundcore               6620  1 snd
parport                32635  3 ppdev,lp,parport_pc
intel_agp              24119  2 i915
agpgart                31724  2 drm,intel_agp
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
output                  1871  1 video
r8169                  34076  0 
mii                     4381  1 r8169
jim@dhcppc1:~$ 

```

---

### Post by sks24 on 2010-11-17
update:  According to [this page]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Commands#lsusb"), if (upon "sudo iwlist wlan1") 
I get the following, then "your device and driver are probably working properly."
That is, in fact, what the command yields.  Still, I don't see any option for connection to "wlan1" in the "Connection Properties" box, and attempts to enable the wireless network using the "configure" tab in the  are unavailing.  

```
jim@dhcppc1:~$ sudo iwlist wlan1 scan
wlan1     Scan completed :
          Cell 01 - Address: 00:0F:66:CD:10:70
                    ESSID:"pete"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.417 GHz (Channel 2)
                    Quality:60/100  Signal level:-57 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
```

Thanks for your help,
Scott

---

### Post by sks24 on 2010-11-17
Another problem: all "gksudo gedit" commands yield gedit docs with no text in the logs.  Just white space.  I've compared the plugin configuration to the one in my 9.10 installation (which works fine), and it's the same absent the "external tools" plugin is enabled in the 10.04 Studio installation.

I can simply type text directly into the the editor, and it renders.

Is there another way to boot the kernel with the pci-noacpi option?  That's what I was trying to do in gedit.  

Let me just say that I always run md5 checksums on the five or so installations which I've done, and they all, including this one, have checked out.

---

### Post by sks24 on 2010-11-17
Another problem: 

I should get either "claimed, unclaimed, enabled, or disabled" upon running "sudo lshw -C network,"  but I get none of them.  Where the output once said "disabled," it now is blank. (Just to make sure, I copy and pasted the output in a doc and ran the "find" feature for each word.)

---

### Post by uncaspi on 2010-11-17
I noticed in dmesg the card was named wlan0 while in iwconfig its named wlan1

---

### Post by sks24 on 2010-11-17
Thanks uncaspi,

That might have happened after I finally got the network manger installed.  I think there might have been an update which had earlier failed, which, upon successfully installing, allowed the NM to install.  

But I'll look into it and see if some renaming is not in order.

This has all been very interesting, but I'm getting to the point where I just want this thing to WORK!  I mean, I've spent hours on this.  The wireless adapter works fine in the XP side of this box, BTW.

Anyway,
Thanks again for your reply.

---

### Post by uncaspi on 2010-11-17
Take a look in /etc/network/interfaces

If you see auto wlan1 
          iface wlan 1 inet ...................
 
it is not handled by the network-manager. You should only have 

auto lo
iface lo inet loopback

if you use nm. Else you must stop nm and bring the cards up manually.

---

### Post by sks24 on 2010-11-17
Thanks uncaspi,

this is what it shows:


# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

Having poked around in google on this, I'm still at a loss as to what I might try next . . .

---

### Post by uncaspi on 2010-11-17
Ok the file tell us that eth0 is not handled by nm.

---

### Post by sks24 on 2010-11-18
thanks uncaspi,

Before I continue, let me just be clear: I'm trying use a D-Link usb wireless adapter on an Ubuntu Studio partition.  The device operates perfectly on the Windows XP side of the same computer. 

Under "connection properties," I show two devices/connections: ethernet (etho0), and loopback interface (lo).  

In network tools, under "Devices," I show three network devices: the two I just mentioned, and a third: "Wireless Interface" (wlan1).

The interface information for wlan1 indicates it is enabled and active, but the statistics show no bytes transmitted or received.

So it looks to me like the ethernet and the loopback interface are being managed by the nm, but not the wlan1.

Do I want the the nm to manage the wireless device?  

If not, how do I bring the card up manually?  

I booted with no-apic, btw, which didn't help with this issue.

Again, thanks for your help with this matter,
Scott

---

### Post by sks24 on 2010-11-18
Also, I cannot disable IPv6 via gedit.

Upon running "gksudo gedit /etc/modprobe.d/aliases", the gedit doc which is generated has no readout.  It's just a blank document.  

I'm doing all this for a friend, he has my backup computer, and, well, it sure would be nice if I could get his tower back to him with Studio on it.  I guess I should have installed it on mine, first, as I'm running 9.10, and need to upgrade anyway.

---

### Post by bkratz on 2010-11-18
I am certainly no expert at this function, but I checked mine and don't have a file named that either, so I used googlubuntu and found this posting which describes either editing or creating that file.

[http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9655682&postcount=7](http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9655682&postcount=7)

So apparently it is not surprising that the file comes up blank (you may have to create it) .

---

### Post by chili555 on 2010-11-18
First, let's be sure Network Manager is not fighting us. Detach the ethernet cable and do:```
sudo ifconfig eth0 down
```Next, let's be sure the wireless driver is in order. Please run and post:```
ndiswrapper -l
dmesg | grep ndis
```That's an l for 'list.'

When you click the Network Manager icon *with the ethernet interface down*, do you see your network? What happens when you click it and try to connect?

Please don't make any more changes until my colleague bkratz and I can tell exactly what it is that's amiss.

---

### Post by sks24 on 2010-11-18
Thanks so much, bkratz & chili555, for chiming in. 


```
jim@dhcppc1:~$ sudo ifconfig eth0 down
[sudo] password for jim: 
jim@dhcppc1:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
net8192su : driver installed
	device (07D1:3300) present
jim@dhcppc1:~$ dmesg | grep ndis
[    8.807788] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[    9.652125] ndiswrapper: driver net8192su (D-Link Corporation,04/08/2009,5.1071.0408.2009) loaded
[   11.397292] usbcore: registered new interface driver ndiswrapper
[   11.428299] ndiswrapper: changing interface name from 'wlan0' to 'wlan1'
jim@dhcppc1:~$ 
```

> When you click the Network Manager icon with the ethernet interface down, do you see your network?

No.  There are no networks listed in either the wired or wireless network.  (The wireless router is less than 25 feet away.)

> What happens when you click it and try to connect?

With the present interface, I don't know how to connect.  (see attached pic)

I won't try anything else till I hear from you.  

Thank you for your help with this.

---

### Post by chili555 on 2010-11-19
Your settings look just perfect! That's bad news because I see nothing obvious to fix. May we see:```
dmesg | grep wlan
sudo iwlist wlan1 scan
```We ought to be seeing some evidence of attempts to connect.

I was not referring to the System > Administration > Network Tools application. I was referring to the Network Manager icon, which shows as two little computer monitors on my system. Please see attached. In other variants of Ubuntu, it may look like an antenna with ripples representing radio waves. 

If you see no such icon, please see here: [http://ubuntuforums.org/showthread.php?t=1571065](http://ubuntuforums.org/showthread.php?t=1571065)

---

### Post by bkratz on 2010-11-19
> **chili555 said:**
> Your settings look just perfect! That's bad news because I see nothing obvious to fix. May we see:```
dmesg | grep wlan
sudo iwlist wlan1 scan
```We ought to be seeing some evidence of attempts to connect.



@Chili--version 1.55 of ndiswrapper was the one I (and a lot of people) had problems with. Perhaps the dmesg above will demonstrate the bug  [https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/459716](https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/459716)

"invalid cmd 12" when attempting to contact to an encrypted network. I believe this is what I would expect to see in his dmesg--

for reference here is the original thread in case this shows up
[http://georgia.ubuntuforums.org/showthread.php?t=1343847](http://georgia.ubuntuforums.org/showthread.php?t=1343847)  it may not.

---

### Post by sks24 on 2010-11-19
Thank you both for your replies,

The interface doesn't allow for a connection to a wireless network.  Clicking on the Network Manager icon in the system tray yields a dialogue box with options to connect to "eth0avahi" and "lo".  No wireless networks are listed.  

```
jim@dhcppc1:~$ dmesg | grep wlan
[   11.033326] wlan0: ethernet device 00:24:01:f0:de:d0 using NDIS driver: net8192su, version: 0x1, NDIS version: 0x500, vendor: 'Realtek RTL8192S Wireless LAN USB NIC                                     ', 07D1:3300.F.conf
[   11.033370] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   11.064160] ndiswrapper: changing interface name from 'wlan0' to 'wlan1'
[   11.064198] udev: renamed network interface wlan0 to wlan1
[   11.065686] ADDRCONF(NETDEV_UP): wlan1: link is not ready
jim@dhcppc1:~$ sudo iwlist wlan1 scan
[sudo] password for jim: 
wlan1     Scan completed :
          Cell 01 - Address: 00:0F:66:CD:10:70
                    ESSID:"pete"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.417 GHz (Channel 2)
                    Quality:60/100  Signal level:-57 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

jim@dhcppc1:~$ 
```

---

### Post by sks24 on 2010-11-19
Well, [this]("http://ubuntuforums.org/showpost.php?p=10117978&postcount=7") looked promising, but gedit is read-only.   "Tools>External Tools>Open terminal here" gives me a terminal, but I'm not sure how to get to changing "managed=false" to "managed=true."  

I'm sorry about having to ask for all this hand-holding.

That said, I will not be defeated by this!

---

### Post by chili555 on 2010-11-19
> "invalid cmd 12" when attempting to contact to an encrypted network. I believe this is what I would expect to see in his dmesg--
Thankfully, we do not. The fact that the interface can scan and sees networks strongly suggests that the driver and card are working as expected. Whether NM and wpa_supplicant are working correctly, we don't yet know.

We wonder why NM is not taking command of the card. What does this tell us?```
cat /etc/network/interfaces
```If wlan1 or even wlan0 is listed in there, remove those lines with:```
sudo gedit /etc/network/interfaces
```Reboot; now does your network show in NM? Did you try the native driver? Is yours a 64-bit system? There is a fix for this issue.

---

### Post by chili555 on 2010-11-19
> **sks24 said:**
> Well, [this]("http://ubuntuforums.org/showpost.php?p=10117978&postcount=7") looked promising, but gedit is read-only.   "Tools>External Tools>Open terminal here" gives me a terminal, but I'm not sure how to get to changing "managed=false" to "managed=true."  

I'm sorry about having to ask for all this hand-holding.

That said, I will not be defeated by this!Hold off on that until we have explored the questions in my post above.

---

### Post by bkratz on 2010-11-19
Well, it certainly is possible to change. When you looked at it with gedit you didn't have permission to change it. Before we try that what exactly did it say? 

[COLOR="DarkRed"]changed "managed=false" to "managed=true"[/COLOR]  did it say false?


Sorry, you are already in the best of hands. Follow whatever Mr. Terminal! says! Was reading the thread when he responded!

---

### Post by sks24 on 2010-11-19
It's a 32 bit system.

Doesn't look like either wlan is in the nm.

```
jim@dhcppc1:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
jim@dhcppc1:~$ 

```

---

### Post by chili555 on 2010-11-19
I suggest you do:```
sudo gedit /etc/network/interfaces
```Amend the file as follows:```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
**#**auto eth0
**#**iface eth0 inet dhcp

```Proofread, save and close gedit. When NM is restarted, whether manually or by reboot, it will show eth0 or wired ethernet as a managed interface. There is no need to do so now, we are interested in wlan1.

That is how you edit read-only (to the ordinary user) files.

I was primarily interested in whether wlan0 or wlan1 was in there and, therefor *not* managed by NM.> changing "managed=false" to "managed=true." That only tells NM to manage or not manage interfaces that are listed in /etc/network/interfaces. With no changes to this switch, interfaces listed in /etc/network/interfaces are NOT managed by NM. With only lo, the loopback interface listed in /etc/network/interfaces, NM should manage everything else; which is what we want.

The question remains; did you try the native driver? Does it exist on your system?```
modinfo r8192s_usb | grep 3300
```

---

### Post by sks24 on 2010-11-19
```
jim@dhcppc1:~$ modinfo r8192s_usb | grep 3300
jim@dhcppc1:~$
```

I followed the instructions for this device (DWA-130) listed [here]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#USB"), and so my impression was that there were no native drivers.  

I now have two network icons on the taskbar.  Clicking on the new one lists the wireless network I'm trying to connect to.  However, upon entering the password it just beachballs and cycles back to the dialogue box requesting a password.

---

### Post by chili555 on 2010-11-19
> Clicking on the new one lists the wireless network I'm trying to connect to. However, upon entering the password it just beachballs and cycles back to the dialogue box requesting a password.Well, sir; now we're gettin' somewhere!

Does it pop up the type of encrytion you actually have? Does the password work seamlessly on other computers on the system? We could look at:```
sudo cat /var/log/syslog | tail -n25
```See if there are any interesting messages from Network Manager involving encryption and passwords.

---

### Post by sks24 on 2010-11-19
I really, really appreciate all your help.  Without you and this community, I'm like the proverbial monkey pecking away with the expectation of Shakespeare.  (That's not exactly it, but you know what I mean.)   

> Does it pop up the type of encrytion you actually have?
WEP 40/128-bit Key.

> Does the password work seamlessly on other computers on the system?
Yes.

> See if there are any interesting messages from Network Manager involving encryption and passwords.

See attached screenshot.

```
jim@dhcppc1:~$ sudo cat /var/log/syslog | tail -n25
Nov 19 14:00:58 dhcppc1 NetworkManager: <info>  dhclient started with pid 1782
Nov 19 14:00:58 dhcppc1 NetworkManager: <info>  Activation (wlan1) Stage 4 of 5 (IP6 Configure Get) scheduled...
Nov 19 14:00:58 dhcppc1 NetworkManager: <info>  Activation (wlan1) Stage 3 of 5 (IP Configure Start) complete.
Nov 19 14:00:58 dhcppc1 NetworkManager: <info>  Activation (wlan1) Stage 4 of 5 (IP6 Configure Get) started...
Nov 19 14:00:58 dhcppc1 NetworkManager: <info>  Activation (wlan1) Stage 4 of 5 (IP6 Configure Get) complete.
Nov 19 14:00:58 dhcppc1 dhclient: Internet Systems Consortium DHCP Client V3.1.3
Nov 19 14:00:58 dhcppc1 dhclient: Copyright 2004-2009 Internet Systems Consortium.
Nov 19 14:00:58 dhcppc1 dhclient: All rights reserved.
Nov 19 14:00:58 dhcppc1 dhclient: For info, please visit https://www.isc.org/software/dhcp/
Nov 19 14:00:58 dhcppc1 dhclient: 
Nov 19 14:00:58 dhcppc1 NetworkManager: <info>  DHCP: device wlan1 state changed normal exit -> preinit
Nov 19 14:00:58 dhcppc1 dhclient: Listening on LPF/wlan1/00:24:01:f0:de:d0
Nov 19 14:00:58 dhcppc1 dhclient: Sending on   LPF/wlan1/00:24:01:f0:de:d0
Nov 19 14:00:58 dhcppc1 dhclient: Sending on   Socket/fallback
Nov 19 14:01:00 dhcppc1 dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 7
Nov 19 14:01:07 dhcppc1 dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 21
Nov 19 14:01:28 dhcppc1 dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 17
Nov 19 14:01:44 dhcppc1 NetworkManager: <info>  (wlan1): DHCP transaction took too long, stopping it.
Nov 19 14:01:44 dhcppc1 NetworkManager: <info>  (wlan1): canceled DHCP transaction, dhcp client pid 1782
Nov 19 14:01:44 dhcppc1 NetworkManager: <info>  Activation (wlan1) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Nov 19 14:01:44 dhcppc1 NetworkManager: <info>  Activation (wlan1) Stage 4 of 5 (IP4 Configure Timeout) started...
Nov 19 14:01:44 dhcppc1 NetworkManager: <info>  Activation (wlan1/wireless): could not get IP configuration for connection 'Auto pete'.
Nov 19 14:01:44 dhcppc1 NetworkManager: <info>  (wlan1): device state change: 7 -> 6 (reason 0)
Nov 19 14:01:44 dhcppc1 NetworkManager: <info>  Activation (wlan1/wireless): asking for new secrets
Nov 19 14:01:44 dhcppc1 NetworkManager: <info>  Activation (wlan1) Stage 4 of 5 (IP4 Configure Timeout) complete.
jim@dhcppc1:~$
```

---

### Post by chili555 on 2010-11-20
It all looks perfect; that is, no obvious errors or defects to try to correct. Everything is just fine until it doesn't connect.

I noticed your scan showed Quality 60/100. That suggests that, either you are some distance from the router (congratulations on your big house!), or interference on channel 2. You might try changing the channel in the router to 1 or 11 or somewhere that shows better quality.

A couple of wireless routers I have owned allow me to manipulate the transmit power, usually in coarse steps, such as 50%, 75% or 100%. You might try increasing the transmit power.

Your router doesn't block by MAC address, does it?

Th driver may not be at sufficient transmit power. Please run:```
iwconfig
```Is the mode 'Managed?' You might try inching the txpower up until it errors out:```
sudo iwconfig wlan1 txpower 15
```If the number takes, try 16, 17, etc. until it errors out.

I am interested in the change from wlan0 to wlan1. May I see:```
cat /etc/udev/rules.d/70-persistent-net.rules
```Are there both letters and numbers in your WEP key? Have you tried both upper and lower case letters in the password box in Ubuntu?

I'm sort of at a loss to try to fix an issue with nothing obviously wrong!

---

### Post by sks24 on 2010-11-20
Check this out: just for the heck of it, I booted with another D-Link wireless usb adapter (WUA-1340) and it connected to the wireless network seamlessly.  

Now, the DWA-130, the one we've been trying to get going, did work on the Windows side of this computer.  So, who knows?  I did run wi-fi inspector, and there's no channel or frequency conflicts with my neighbors, so that probably isn't a problem.  

So I'll just leave the 1340 in and consider this solved and blame everything on a bad device.

One loose end: there are two network connection icons in the taskbar, and one reads "Network Connection:etho:avahi error" when I mouse over it.  The other network icon - we're talking the two little monitors - is for the wireless network.

I ran "sudo ifconfig eth0 up", but that didn't get me to where I would like to be, which is just one network icon in the taskbar.

The ethernet does work fine the way things are (I can load pages and so forth), but this computer is for a complete Ubuntu newbie, so I want the interface to be as simple as possible for him.

So, could you help me with this last little problem? 

Thanks so much for all your help!

Scott

---

### Post by chili555 on 2010-11-20
Does the second icon, "Network Connection:etho:avahi error" look like the attached? If you right-click it and select 'About,' does it say Network Monitor 2.28.1?

It is simply a monitor icon; it does not assist or prevent connection. It simply indicates if you are connected. You don't really need both this and Network Manager. 

The part about eth0:avahi error is simply telling you that there is no cable attached and we couldn't get an IP address.

You may safely right-click it and select 'Remove from panel.' You don't need both. Solved?

---

### Post by sks24 on 2010-11-21
> Solved?

Yesssir; 'tis.

I can't thank you enough, chili.  This installation really had me freaked, and you just flat-out saved the day.

---

### Post by chili555 on 2010-11-21
'twas my pleasure. It looks like I could have walked over to fix it right there in SC. Glad it's working.

---

