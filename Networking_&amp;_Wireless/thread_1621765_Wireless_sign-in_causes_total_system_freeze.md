---
title: "Wireless sign-in causes total system freeze"
date: 2010-11-14
forum: Networking &amp; Wireless
---

### Post by TheFlyingOx on 2010-11-14
Ubuntu boots fine with wireless turned off via the laptop wireless button on the case, and fine with wireless on but no networks remembered, but as soon as I try to connect to a network, I get the strobing wireless icon in the top panel and then the whole system freezes. It switches to a black screen with a non-flashing terminal cursor in the top left corner of the screen plus a frozen mouse pointer in the last position from when Ubuntu was working. If I force a power-off after this, which I have to, then unless I manually turn off wifi using the laptop button then Ubuntu never boots and I just get a black screen after the BIOS screen. I can connect to the internet via wired connection.

Outputs from terminal based on what's suggested in the sticky are:
(sorry it's long, but I really don't know which bit you guys are looking for in order to work out the problem)

---

### Post by TheFlyingOx on 2010-11-14
$ lspci
09:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
09:04.0 Network controller: RaLink RT2561/RT61 rev B 802.11g

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:0a:5f:a8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:9 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:0d:f0:38:0d:4b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=11 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

$ lsmod
Module                  Size  Used by
parport_pc             26058  0 
ppdev                   5556  0 
binfmt_misc             6599  1 
joydev                  8735  0 
snd_hda_codec_realtek   217980  1 
snd_hda_intel          22107  2 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
radeon                825934  3 
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
arc4                    1165  2 
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
ttm                    56633  1 radeon
snd_seq_midi_event      6047  1 snd_seq_midi
rt61pci                18996  0 
drm_kms_helper         30200  1 radeon
crc_itu_t               1383  1 rt61pci
rt2x00pci               6029  1 rt61pci
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
rt2x00lib              27275  2 rt61pci,rt2x00pci
led_class               2633  1 rt2x00lib
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              231541  2 rt2x00pci,rt2x00lib
drm                   168054  5 radeon,ttm,drm_kms_helper
i2c_algo_bit            5168  1 radeon
cfg80211              144470  2 rt2x00lib,mac80211
snd                    49006  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 29886  0 
ati_agp                 5202  0 
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
psmouse                59033  0 
serio_raw               4022  0 
eeprom_93cx6            1345  1 rt61pci
i2c_piix4               8635  0 
agpgart                32011  3 ttm,drm,ati_agp
video                  18712  0 
output                  1883  1 video
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
8139too                19581  0 
sata_sil                7035  2 
pata_atiixp             3288  0 
8139cp                 16934  0 
mii                     4425  2 8139too,8139cp

---

### Post by TheFlyingOx on 2010-11-14
$ dmesg
[    0.011105] ACPI: Core revision 20100428
[    0.020011] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.020020] ftrace: allocating 21758 entries in 43 pages
[    0.024090] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.024458] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.064170] CPU0: Genuine Intel(R) CPU           T2080  @ 1.73GHz stepping 0c
[    0.068000] Booting Node   0, Processors  #1 Ok.
[    0.008000] Initializing CPU#1
[    0.156029] Brought up 2 CPUs
[    0.156034] Total of 2 processors activated (6934.17 BogoMIPS).
[    0.156588] devtmpfs: initialized
[    0.157311] regulator: core version 0.5
[    0.157350] Time: 20:58:38  Date: 11/14/10
[    0.157405] NET: Registered protocol family 16
[    0.157449] Trying to unpack rootfs image as initramfs...
[    0.157591] EISA bus registered
[    0.157604] ACPI: bus type pci registered
[    0.157711] PCI: MMCONFIG for domain 0000 [bus 00-0d] at [mem 0xe0000000-0xe0dfffff] (base 0xe0000000)
[    0.157716] PCI: MMCONFIG at [mem 0xe0000000-0xe0dfffff] reserved in E820
[    0.157718] PCI: Using MMCONFIG for extended config space
[    0.157721] PCI: Using configuration type 1 for base access
[    0.164196] bio: create slab <bio-0> at 0
[    0.165895] ACPI: EC: Look up EC in DSDT
[    0.170600] ACPI: SSDT 37e91aa4 001E8 (v01  PmRef  Cpu0Ist 00003000 INTL 20050228)
[    0.171020] ACPI: Dynamic OEM Table Load:
[    0.171024] ACPI: SSDT (null) 001E8 (v01  PmRef  Cpu0Ist 00003000 INTL 20050228)
[    0.171880] ACPI: SSDT 37e9182f 001F0 (v01  PmRef  Cpu0Cst 00003001 INTL 20050228)
[    0.172340] ACPI: Dynamic OEM Table Load:
[    0.172345] ACPI: SSDT (null) 001F0 (v01  PmRef  Cpu0Cst 00003001 INTL 20050228)
[    0.172856] ACPI: SSDT 37e91c8c 00087 (v01  PmRef  Cpu1Ist 00003000 INTL 20050228)
[    0.173262] ACPI: Dynamic OEM Table Load:
[    0.173267] ACPI: SSDT (null) 00087 (v01  PmRef  Cpu1Ist 00003000 INTL 20050228)
[    0.173448] ACPI: SSDT 37e91a1f 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050228)
[    0.173843] ACPI: Dynamic OEM Table Load:
[    0.173848] ACPI: SSDT (null) 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050228)
[    0.252106] ACPI: Interpreter enabled
[    0.252126] ACPI: (supports S0 S3 S4 S5)
[    0.252167] ACPI: Using IOAPIC for interrupt routing
[    0.258248] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[    0.258491] ACPI: No dock devices found.
[    0.258498] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.259237] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.260661] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.260666] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000d3fff] (ignored)
[    0.260670] pci_root PNP0A03:00: host bridge window [mem 0x000d4000-0x000d7fff] (ignored)
[    0.260673] pci_root PNP0A03:00: host bridge window [mem 0x000d8000-0x000dbfff] (ignored)
[    0.260677] pci_root PNP0A03:00: host bridge window [mem 0x38000000-0xfebfffff] (ignored)
[    0.260681] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.260684] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.260877] pci 0000:00:12.0: reg 10: [io  0x8440-0x8447]
[    0.260891] pci 0000:00:12.0: reg 14: [io  0x8430-0x8433]
[    0.260902] pci 0000:00:12.0: reg 18: [io  0x8420-0x8427]
[    0.260917] pci 0000:00:12.0: reg 1c: [io  0x8410-0x8413]
[    0.260928] pci 0000:00:12.0: reg 20: [io  0x8400-0x840f]
[    0.260939] pci 0000:00:12.0: reg 24: [mem 0xc0407000-0xc04071ff]
[    0.260950] pci 0000:00:12.0: reg 30: [mem 0x00000000-0x0007ffff pref]
[    0.260992] pci 0000:00:12.0: supports D1 D2
[    0.261035] pci 0000:00:13.0: reg 10: [mem 0xc0404000-0xc0404fff]
[    0.261132] pci 0000:00:13.1: reg 10: [mem 0xc0405000-0xc0405fff]
[    0.261243] pci 0000:00:13.2: reg 10: [mem 0xc0406000-0xc0406fff]
[    0.261328] pci 0000:00:13.2: supports D1 D2
[    0.261331] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.261338] pci 0000:00:13.2: PME# disabled
[    0.261384] pci 0000:00:14.0: reg 10: [io  0x8040-0x804f]
[    0.261395] pci 0000:00:14.0: reg 14: [mem 0xc0407400-0xc04077ff]
[    0.261442] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.261492] pci 0000:00:14.1: reg 10: [io  0x01f0-0x01f7]
[    0.261503] pci 0000:00:14.1: reg 14: [io  0x03f4-0x03f7]
[    0.261514] pci 0000:00:14.1: reg 18: [io  0x0170-0x0177]
[    0.261524] pci 0000:00:14.1: reg 1c: [io  0x0374-0x0377]
[    0.261536] pci 0000:00:14.1: reg 20: [io  0x8460-0x846f]
[    0.261652] pci 0000:00:14.2: reg 10: [mem 0xc0400000-0xc0403fff 64bit]
[    0.261737] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.261743] pci 0000:00:14.2: PME# disabled
[    0.261969] pci 0000:01:05.0: reg 10: [mem 0xd0000000-0xdfffffff pref]
[    0.261975] pci 0000:01:05.0: reg 14: [io  0x9000-0x90ff]
[    0.261982] pci 0000:01:05.0: reg 18: [mem 0xc0000000-0xc000ffff]
[    0.261999] pci 0000:01:05.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.262018] pci 0000:01:05.0: supports D1 D2
[    0.262055] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.262065] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    0.262070] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xc00fffff]
[    0.262075] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff pref]
[    0.262159] pci 0000:09:02.0: reg 10: [io  0xa000-0xa0ff]
[    0.262171] pci 0000:09:02.0: reg 14: [mem 0xc0100000-0xc01000ff]
[    0.262256] pci 0000:09:02.0: supports D1 D2
[    0.262259] pci 0000:09:02.0: PME# supported from D1 D2 D3hot D3cold
[    0.262266] pci 0000:09:02.0: PME# disabled
[    0.262327] pci 0000:09:04.0: reg 10: [mem 0xc0108000-0xc010ffff]
[    0.262498] pci 0000:00:14.4: PCI bridge to [bus 09-0e] (subtractive decode)
[    0.262510] pci 0000:00:14.4:   bridge window [io  0xa000-0xafff]
[    0.262518] pci 0000:00:14.4:   bridge window [mem 0xf0200000-0xf02fffff]
[    0.262527] pci 0000:00:14.4:   bridge window [mem 0xf0300000-0xf03fffff pref]
[    0.262533] pci 0000:00:14.4:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.262536] pci 0000:00:14.4:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[    0.262558] pci_bus 0000:00: on NUMA node 0
[    0.262570] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.262866] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.263020] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.266156] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[    0.266295] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[    0.266429] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[    0.266558] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[    0.266688] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[    0.266826] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[    0.266966] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[    0.267097] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[    0.267157] HEST: Table is not found!
[    0.267323] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.267330] vgaarb: loaded
[    0.267589] SCSI subsystem initialized
[    0.267749] libata version 3.00 loaded.
[    0.267845] usbcore: registered new interface driver usbfs
[    0.267862] usbcore: registered new interface driver hub
[    0.267905] usbcore: registered new device driver usb
[    0.268117] ACPI: WMI: Mapper loaded
[    0.268120] PCI: Using ACPI for IRQ routing
[    0.268126] PCI: pci_cache_line_size set to 64 bytes
[    0.268225] reserve RAM buffer: 0000000000002000 - 000000000000ffff 
[    0.268229] reserve RAM buffer: 000000000009dc00 - 000000000009ffff 
[    0.268233] reserve RAM buffer: 0000000037e90000 - 0000000037ffffff 
[    0.268405] NetLabel: Initializing
[    0.268408] NetLabel:  domain hash size = 128
[    0.268410] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.268428] NetLabel:  unlabeled traffic allowed by default
[    0.268497] Switching to clocksource tsc
[    0.284100] AppArmor: AppArmor Filesystem Enabled
[    0.284154] pnp: PnP ACPI init
[    0.284194] ACPI: bus type pnp registered
[    0.286440] pnp 00:09: disabling [mem 0x00000000-0x00000fff] because it overlaps 0000:00:12.0 BAR 6 [mem 0x00000000-0x0007ffff pref]
[    0.286456] pnp 00:09: disabling [mem 0x00000000-0x00000fff disabled] because it overlaps 0000:01:05.0 BAR 6 [mem 0x00000000-0x0001ffff pref]
[    0.286685] pnp: PnP ACPI: found 10 devices
[    0.286688] ACPI: ACPI bus type pnp unregistered
[    0.286695] PnPBIOS: Disabled by ACPI PNP
[    0.286714] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.286725] system 00:08: [io  0x1080] has been reserved
[    0.286730] system 00:08: [io  0x0200-0x020f] has been reserved
[    0.286733] system 00:08: [io  0x040b] has been reserved
[    0.286737] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.286741] system 00:08: [io  0x04d6] has been reserved
[    0.286745] system 00:08: [io  0x0530-0x0537] has been reserved
[    0.286748] system 00:08: [io  0x0c00-0x0c01] has been reserved
[    0.286752] system 00:08: [io  0x0c14] has been reserved
[    0.286755] system 00:08: [io  0x0c50-0x0c52] has been reserved
[    0.286759] system 00:08: [io  0x0c6c] has been reserved
[    0.286763] system 00:08: [io  0x0c6f] has been reserved
[    0.286766] system 00:08: [io  0x0cd4-0x0cd5] has been reserved
[    0.286770] system 00:08: [io  0x0cd6-0x0cd7] has been reserved
[    0.286774] system 00:08: [io  0x0cd8-0x0cdf] has been reserved
[    0.286778] system 00:08: [io  0x8000-0x805f] could not be reserved
[    0.286782] system 00:08: [io  0x8100-0x81ff window] has been reserved
[    0.286786] system 00:08: [io  0x0f40-0x0f47] has been reserved
[    0.286789] system 00:08: [io  0x0280-0x0293] has been reserved
[    0.286793] system 00:08: [io  0x087f] has been reserved
[    0.286800] system 00:09: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.286805] system 00:09: [mem 0xfff80000-0xffffffff] has been reserved
[    0.323492] pci 0000:00:12.0: BAR 6: assigned [mem 0x38000000-0x3807ffff pref]
[    0.323502] pci 0000:01:05.0: BAR 6: assigned [mem 0xc0020000-0xc003ffff pref]
[    0.323506] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.323510] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    0.323517] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xc00fffff]
[    0.323522] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff pref]
[    0.323530] pci 0000:00:14.4: PCI bridge to [bus 09-0e]
[    0.323535] pci 0000:00:14.4:   bridge window [io  0xa000-0xafff]
[    0.323544] pci 0000:00:14.4:   bridge window [mem 0xf0200000-0xf02fffff]
[    0.323551] pci 0000:00:14.4:   bridge window [mem 0xf0300000-0xf03fffff pref]
[    0.323587] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.323590] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.323594] pci_bus 0000:01: resource 0 [io  0x9000-0x9fff]
[    0.323597] pci_bus 0000:01: resource 1 [mem 0xc0000000-0xc00fffff]
[    0.323601] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff pref]
[    0.323604] pci_bus 0000:09: resource 0 [io  0xa000-0xafff]
[    0.323608] pci_bus 0000:09: resource 1 [mem 0xf0200000-0xf02fffff]
[    0.323611] pci_bus 0000:09: resource 2 [mem 0xf0300000-0xf03fffff pref]
[    0.323614] pci_bus 0000:09: resource 4 [io  0x0000-0xffff]
[    0.323618] pci_bus 0000:09: resource 5 [mem 0x00000000-0xffffffff]
[    0.323706] NET: Registered protocol family 2
[    0.323817] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.324309] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.326210] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.327387] TCP: Hash tables configured (established 131072 bind 65536)
[    0.327394] TCP reno registered
[    0.327404] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.327442] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.327724] NET: Registered protocol family 1
[    0.327759] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    0.327867] pci 0000:01:05.0: Boot video device
[    0.327880] PCI: CLS 32 bytes, default 64
[    0.328218] cpufreq-nforce2: No nForce2 chipset.
[    0.328260] Scanning for low memory corruption every 60 seconds
[    0.328550] audit: initializing netlink socket (disabled)
[    0.328569] type=2000 audit(1289768317.324:1): initialized
[    0.342041] highmem bounce pool size: 64 pages
[    0.342050] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.344927] VFS: Disk quotas dquot_6.5.2
[    0.345030] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.345888] fuse init (API version 7.14)
[    0.346015] msgmni has been set to 1712
[    0.346480] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.346485] io scheduler noop registered
[    0.346488] io scheduler deadline registered
[    0.346507] io scheduler cfq registered (default)
[    0.346678] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.346707] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.346840] intel_idle: MWAIT substates: 0x1110
[    0.346843] intel_idle: does not run on family 6 model 14
[    0.350295] ACPI: AC Adapter [ACAD] (off-line)
[    0.350426] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.350484] ACPI: Lid Switch [LID]
[    0.350546] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.350552] ACPI: Power Button [PWRB]
[    0.350608] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.350613] ACPI: Power Button [PWRF]
[    0.350830] ACPI: acpi_idle registered with cpuidle
[    0.351078] Marking TSC unstable due to TSC halts in idle
[    0.351379] Switching to clocksource acpi_pm
[    0.400864] thermal LNXTHERM:01: registered as thermal_zone0
[    0.400883] ACPI: Thermal Zone [THRM] (55 C)
[    0.401050] ERST: Table is not found!
[    0.401340] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.403365] brd: module loaded
[    0.404160] loop: module loaded
[    0.404541] pata_acpi 0000:00:12.0: enabling device (0005 -> 0007)
[    0.404560]   alloc irq_desc for 22 on node -1
[    0.404563]   alloc kstat_irqs on node -1
[    0.404575] pata_acpi 0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    0.404682]   alloc irq_desc for 16 on node -1
[    0.404685]   alloc kstat_irqs on node -1
[    0.404690] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.404716] pata_acpi 0000:00:14.1: setting latency timer to 64
[    0.405130] Fixed MDIO Bus: probed
[    0.405174] PPP generic driver version 2.4.2
[    0.405248] tun: Universal TUN/TAP device driver, 1.6
[    0.405251] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.405364] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.405395]   alloc irq_desc for 19 on node -1
[    0.405397]   alloc kstat_irqs on node -1
[    0.405403] ehci_hcd 0000:00:13.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.405431] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    0.405477] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[    0.405573] ehci_hcd 0000:00:13.2: irq 19, io mem 0xc0406000
[    0.405789] ACPI: Battery Slot [BAT1] (battery absent)
[    0.405816] isapnp: Scanning for PnP cards...
[    0.455481] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.455765] hub 1-0:1.0: USB hub found
[    0.455774] hub 1-0:1.0: 8 ports detected
[    0.455917] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.455955] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.455985] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.456106] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    0.456142] ohci_hcd 0000:00:13.0: irq 19, io mem 0xc0404000
[    0.531779] Freeing initrd memory: 10508k freed
[    0.545702] hub 2-0:1.0: USB hub found
[    0.545745] hub 2-0:1.0: 4 ports detected
[    0.546179] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.546287] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    0.546749] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    0.546873] ohci_hcd 0000:00:13.1: irq 19, io mem 0xc0405000
[    0.604337] hub 3-0:1.0: USB hub found
[    0.604354] hub 3-0:1.0: 4 ports detected
[    0.604464] uhci_hcd: USB Universal Host Controller Interface driver
[    0.604632] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    0.607278] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.607290] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.607460] mice: PS/2 mouse device common for all mice
[    0.607685] rtc_cmos 00:04: RTC can wake from S4
[    0.607748] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.607787] rtc0: alarms up to one month, 114 bytes nvram
[    0.607947] device-mapper: uevent: version 1.0.3
[    0.608135] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]
[    0.608238] device-mapper: multipath: version 1.1.1 loaded
[    0.608242] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.608407] EISA: Probing bus 0 at eisa.0
[    0.608422] Cannot allocate resource for EISA slot 1
[    0.608455] Cannot allocate resource for EISA slot 8
[    0.608458] EISA: Detected 0 cards.
[    0.608658] cpuidle: using governor ladder
[    0.608797] cpuidle: using governor menu
[    0.609250] TCP cubic registered
[    0.609427] NET: Registered protocol family 10
[    0.609931] lo: Disabled Privacy Extensions
[    0.610235] NET: Registered protocol family 17
[    0.610716] Using IPI No-Shortcut mode
[    0.610829] PM: Resume from disk failed.
[    0.610849] registered taskstats version 1
[    0.611084]   Magic number: 2:647:1003
[    0.611119] input input0: hash matches
[    0.611141] vc vcs: hash matches
[    0.611148] pnp 00:05: hash matches
[    0.611232] rtc_cmos 00:04: setting system clock to 2010-11-14 20:58:39 UTC (1289768319)
[    0.611237] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.611239] EDD information not available.
[    0.639025] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.766402] isapnp: No Plug & Play device found
[    0.766446] Freeing unused kernel memory: 684k freed
[    0.767177] Write protecting the kernel text: 4932k
[    0.767261] Write protecting the kernel read-only data: 1976k
[    0.790068] udev[77]: starting version 163
[    0.918353] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    0.918397] 8139cp 0000:09:02.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    0.957825] scsi0 : pata_atiixp
[    0.958147] scsi1 : pata_atiixp
[    0.958638] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8460 irq 14
[    0.958643] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8468 irq 15
[    0.958874] sata_sil 0000:00:12.0: version 2.4
[    0.959208] scsi2 : sata_sil
[    0.959332] scsi3 : sata_sil
[    0.959679] ata3: SATA max UDMA/100 mmio m512@0xc0407000 tf 0xc0407080 irq 22
[    0.959685] ata4: SATA max UDMA/100 mmio m512@0xc0407000 tf 0xc04070c0 irq 22
[    0.960259] 8139too: 8139too Fast Ethernet driver 0.9.28
[    0.960322] 8139too 0000:09:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 9
[    0.962109] 8139too 0000:09:02.0: eth0: RealTek RTL8139 at 0xa000, 00:1b:24:0a:5f:a8, IRQ 9
[    1.120741] ata2.00: ATAPI: DVD-ROM UJDA780, 1.50, max UDMA/33
[    1.136706] ata2.00: configured for UDMA/33
[    1.138477] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-ROM UJDA780  1.50 PQ: 0 ANSI: 5
[    1.141389] sr0: scsi3-mmc drive: 24x/24x cd/rw xa/form2 cdda tray
[    1.141394] Uniform CD-ROM driver Revision: 3.20
[    1.141567] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.141677] sr 1:0:0:0: Attached scsi generic sg0 type 5
[    1.276104] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.284528] ata3.00: ATA-7: ST980811AS, 3.ALC, max UDMA/133
[    1.284532] ata3.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.301479] ata3.00: configured for UDMA/100
[    1.301691] scsi 2:0:0:0: Direct-Access     ATA      ST980811AS       3.AL PQ: 0 ANSI: 5
[    1.301897] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.302016] sd 2:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.302239] sd 2:0:0:0: [sda] Write Protect is off
[    1.302244] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.302337] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.302811]  sda: sda1 sda2 < sda5 >
[    1.335578] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.620091] ata4: SATA link down (SStatus 0 SControl 300)
[    1.975432] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    1.975439] EXT4-fs (sda1): write access will be enabled during recovery
[    2.115443] EXT4-fs (sda1): recovery complete
[    2.115797] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   15.319094] udev[312]: starting version 163
[   15.364802] lp: driver loaded but no devices found
[   15.455850] Adding 3069948k swap on /dev/sda5.  Priority:-1 extents:1 across:3069948k 
[   15.517717] acpi device:1c: registered as cooling_device2
[   15.517879] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:1a/LNXVIDEO:00/input/input4
[   15.518014] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   15.726263] EXT4-fs (sda1): warning: maximal mount count reached, running e2fsck is recommended
[   15.726530] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   15.822890] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8040, revision 0
[   15.894849] Linux agpgart interface v0.103
[   15.938987] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.010681] cfg80211: Calling CRDA to update world regulatory domain
[   16.095728] cfg80211: World regulatory domain updated:
[   16.095735]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   16.095739]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.095743]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.095747]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.095751]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.095754]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.134207] [drm] Initialized drm 1.1.0 20060810
[   16.145905] rt61pci 0000:09:04.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   16.156968] type=1400 audit(1289768335.043:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=651 comm="apparmor_parser"
[   16.157757] type=1400 audit(1289768335.043:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=651 comm="apparmor_parser"
[   16.158196] type=1400 audit(1289768335.043:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=651 comm="apparmor_parser"
[   16.260556] eth0: link down
[   16.268606] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.312814] phy0: Selected rate control algorithm 'minstrel'
[   16.313789] Registered led device: rt61pci-phy0::radio
[   16.313816] Registered led device: rt61pci-phy0::assoc
[   16.319972] [drm] radeon defaulting to kernel modesetting.
[   16.319978] [drm] radeon kernel modesetting enabled.
[   16.320092]   alloc irq_desc for 17 on node -1
[   16.320095]   alloc kstat_irqs on node -1
[   16.320107] radeon 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.324333] [drm] initializing kernel modesetting (RS400 0x1002:0x5A62).
[   16.363741] [drm] register mmio base: 0xC0000000
[   16.363746] [drm] register mmio size: 65536
[   16.363957] [drm:rs400_gart_adjust_size] *ERROR* Forcing to 32M GART size (because of ASIC bug ?)
[   16.364027] [drm] Generation 2 PCI interface, using max accessible memory
[   16.364035] radeon 0000:01:05.0: VRAM: 128M 0x38000000 - 0x3FFFFFFF (128M used)
[   16.364040] radeon 0000:01:05.0: GTT: 32M 0x40000000 - 0x41FFFFFF
[   16.364109] [drm] radeon: irq initialized.
[   16.364555] [drm] Detected VRAM RAM=128M, BAR=256M
[   16.364561] [drm] RAM width 128bits DDR
[   16.366976] [TTM] Zone  kernel: Available graphics memory: 444044 kiB.
[   16.366981] [TTM] Zone highmem: Available graphics memory: 447408 kiB.
[   16.366984] [TTM] Initializing pool allocator.
[   16.367027] [drm] radeon: 128M of VRAM memory ready
[   16.367031] [drm] radeon: 32M of GTT memory ready.
[   16.367068] [drm] GART: num cpu pages 8192, num gpu pages 8192
[   16.368904] [drm] radeon: 1 quad pipes, 1 z pipes initialized.
[   16.369389] [drm] Loading R300 Microcode
[   16.373485] type=1400 audit(1289768335.259:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=756 comm="apparmor_parser"
[   16.374265] type=1400 audit(1289768335.259:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=756 comm="apparmor_parser"
[   16.374997] type=1400 audit(1289768335.259:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=756 comm="apparmor_parser"
[   16.376369] type=1400 audit(1289768335.263:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=755 comm="apparmor_parser"
[   16.379120] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.379205]   alloc irq_desc for 40 on node -1
[   16.379208]   alloc kstat_irqs on node -1
[   16.379228] HDA Intel 0000:00:14.2: irq 40 for MSI/MSI-X
[   16.380469] [drm] radeon: ring at 0x0000000040000000
[   16.380499] [drm] ring test succeeded in 1 usecs
[   16.380712] [drm] radeon: ib pool ready.
[   16.380828] [drm] ib test succeeded in 0 usecs
[   16.381017] [drm] Panel ID String: LPL                     
[   16.381020] [drm] Panel Size 1280x800
[   16.381089] [drm] Radeon Display Connectors
[   16.381091] [drm] Connector 0:
[   16.381093] [drm]   VGA
[   16.381097] [drm]   DDC: 0x68 0x68 0x68 0x68 0x68 0x68 0x68 0x68
[   16.381099] [drm]   Encoders:
[   16.381102] [drm]     CRT1: INTERNAL_DAC2
[   16.381104] [drm] Connector 1:
[   16.381106] [drm]   LVDS
[   16.381109] [drm]   DDC: 0x198 0x198 0x19c 0x19c 0x1a0 0x1a0 0x1a4 0x1a4
[   16.381112] [drm]   Encoders:
[   16.381114] [drm]     LCD1: INTERNAL_LVDS
[   16.386171] type=1400 audit(1289768335.271:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=761 comm="apparmor_parser"
[   16.387134] type=1400 audit(1289768335.271:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=761 comm="apparmor_parser"
[   16.390455] type=1400 audit(1289768335.275:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=762 comm="apparmor_parser"
[   16.532563] [drm] fb mappable at 0xD0040000
[   16.532567] [drm] vram apper at 0xD0000000
[   16.532570] [drm] size 4096000
[   16.532572] [drm] fb depth is 24
[   16.532574] [drm]    pitch is 5120
[   16.575806] Console: switching to colour frame buffer device 160x50
[   16.581229] fb0: radeondrmfb frame buffer device
[   16.581231] drm: registered panic notifier
[   16.581235] Slow work thread pool: Starting up
[   16.581869] Slow work thread pool: Ready
[   16.581887] [drm] Initialized radeon 2.5.0 20080528 for 0000:01:05.0 on minor 0
[   16.593504] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.631985] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04713/0x0/0x0
[   16.670693] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
[   16.790860] ppdev: user-space parallel port driver
[   17.704969] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
[   21.260649] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
[   41.964963] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   42.048938] ADDRCONF(NETDEV_UP): wlan0: link is not ready

$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:09:02.0
       logical name: eth0
       version: 10
       serial: 00:1b:24:0a:5f:a8
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:9 ioport:a000(size=256) memory:c0100000-c01000ff
  *-network:1
       description: Wireless interface
       product: RT2561/RT61 rev B 802.11g
       vendor: RaLink
       physical id: 4
       bus info: pci@0000:09:04.0
       logical name: wlan0
       version: 00
       serial: 00:0d:f0:38:0d:4b
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci driverversion=2.6.35-22-generic firmware=N/A latency=64 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:22 memory:c0108000-c010ffff

$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

$ lsb_release -d
Description:    Ubuntu 10.10

$ uname -mr
2.6.35-22-generic i686

---

### Post by TheFlyingOx on 2010-11-14
Oh, and it's a Packard Bell Easynote

Thanks.

---

### Post by choongii on 2010-12-29
Hello,

I had the same issue for weeks, and just solved it. I had exactly the same symptoms: could log in, but after wifi established, my screen would go black and I'd get a non-flashing cursor in the upper left corner of the screen.

For me, this was caused by my network card (using ra61pci driver) entered powersaving mode. When I was on AC power, I had no issues, but as soon as I would unplug AC and my laptop switched to battery, the command 'pm-powersave' would execute the script /usr/lib/pm-utils/power.d/wireless. Essentially this would set wlan0's powersaving mode On, which would in turn hang my system.

To override this behaviour, sudo touch /etc/pm/power.d/wireless. This will stop the script from executing.

---

### Post by grahammechanical on 2010-12-29
I do not have the answer but from the listings you supply I can tell you this:

ifconfig shows eth0 and wlan0 as UP. It should also show RUNNING and a inet addr that is the same as the address of the router/modem. You do not have an inet addr. You are not connected to the modem.

iwconfig shows ESSID to be off. It should show the name of your Internet connection. It also says Access Point Not Associated.  This says you are not connected to the modem.

lshw -C net has link=no. This is why iwlist scan says wlan0 No scan results.

The wireless adapter is not connected to the router/modem because it is not switched on. This is my guess. Something is happening to your display. It seems that you a being dropped to a command line prompt. You may have a faulty display adapter. Or faulty memory chips.

Regards.

---

