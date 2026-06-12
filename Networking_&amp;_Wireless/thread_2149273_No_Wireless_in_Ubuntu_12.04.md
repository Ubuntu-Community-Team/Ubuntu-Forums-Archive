---
title: "No Wireless in Ubuntu 12.04"
date: 2013-05-28
forum: Networking &amp; Wireless
---

### Post by PDA1 on 2013-05-28
No wireless connection- I'm pulling my hair out. Some guy recommended I "upgrade" to 12.04 from 10.04 (netbook) to get the wireless working. Big mistake! Ethernet works fine- wireless doesn't work at all. All of the following commands were issued while connected to the web with ethernet.

Here's what my computer says;

```
$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GSE Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)
```

```
$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 002 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
```

```
$ lspci -nn | grep AR542x
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
```

```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:8b:6e:b0:36  
          inet addr:192.168.1.15  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:8bff:fe6e:b036/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15452 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8841 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21076804 (21.0 MB)  TX bytes:780806 (780.8 KB)
          Interrupt:44 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1214 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1214 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:107496 (107.4 KB)  TX bytes:107496 (107.4 KB)
```

```
$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.
```

```
$ iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

```
$ lsmod
Module                  Size  Used by
dm_crypt               22528  0 
joydev                 17393  0 
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
psmouse                96718  0 
arc4                   12473  2 
serio_raw              13027  0 
ath5k                 145127  0 
ath                    19387  1 ath5k
mac80211              436493  1 ath5k
snd_hda_codec_realtek   174313  1 
cfg80211              178877  3 ath5k,ath,mac80211
snd_hda_intel          32719  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec
rfcomm                 38139  0 
bnep                   17830  2 
parport_pc             32114  0 
bluetooth             158479  10 rfcomm,bnep
ppdev                  12849  0 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62218  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
binfmt_misc            17292  1 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41937  0 
hid                    77428  1 usbhid
wmi                    18744  0 
r8169                  56368  0 
i915                  427979  2 
drm_kms_helper         45466  1 i915
drm                   197641  3 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  19115  1 i915
```

```
$ lsmod | grep wlan0

The command was supposed to be $ lsmod | grep "wlan_module_name", but since I have no idea what they're talking about in the BEFORE YOUR POST topic I have no idea what to enter here.
```

```
$ dmesg

[    0.430322] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.440217] Switching to clocksource hpet
[    0.465482] AppArmor: AppArmor Filesystem Enabled
[    0.465568] pnp: PnP ACPI init
[    0.465626] ACPI: bus type pnp registered
[    0.466974] pnp 00:00: [bus 00-ff]
[    0.466992] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.467001] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.467010] pnp 00:00: [io  0x0d00-0xffff window]
[    0.467020] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.467030] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.467039] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.467049] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.467059] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.467069] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.467079] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.467089] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.467099] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.467109] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.467119] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.467128] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.467137] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.467146] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.467156] pnp 00:00: [mem 0x20000000-0xfebfffff window]
[    0.467351] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.467837] pnp 00:01: [io  0x002e-0x002f]
[    0.467847] pnp 00:01: [io  0x0068-0x006f]
[    0.467856] pnp 00:01: [io  0x0200-0x020f]
[    0.467864] pnp 00:01: [io  0x164e-0x164f]
[    0.467871] pnp 00:01: [io  0x0061]
[    0.467879] pnp 00:01: [io  0x0070]
[    0.467886] pnp 00:01: [io  0x0080]
[    0.467894] pnp 00:01: [io  0x0092]
[    0.467902] pnp 00:01: [io  0x00b2-0x00b3]
[    0.467909] pnp 00:01: [io  0x0063]
[    0.467916] pnp 00:01: [io  0x0065]
[    0.467923] pnp 00:01: [io  0x0067]
[    0.467932] pnp 00:01: [io  0x0600-0x060f]
[    0.467940] pnp 00:01: [io  0x0610]
[    0.467948] pnp 00:01: [io  0x0800-0x080f]
[    0.467957] pnp 00:01: [io  0x0400-0x047f]
[    0.467965] pnp 00:01: [io  0x0500-0x053f]
[    0.467974] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    0.467984] pnp 00:01: [mem 0xfed1c000-0xfed1ffff]
[    0.467992] pnp 00:01: [mem 0xfed14000-0xfed17fff]
[    0.468052] pnp 00:01: [mem 0xfed18000-0xfed18fff]
[    0.468061] pnp 00:01: [mem 0xfed19000-0xfed19fff]
[    0.468070] pnp 00:01: [mem 0xfec00000-0xfec00fff]
[    0.468078] pnp 00:01: [mem 0xfee00000-0xfee00fff]
[    0.468141] pnp 00:01: disabling [io  0x164e-0x164f] because it overlaps 0000:00:1c.3 BAR 13 [io  0x1000-0x1fff]
[    0.468346] system 00:01: [io  0x0200-0x020f] has been reserved
[    0.468359] system 00:01: [io  0x0600-0x060f] has been reserved
[    0.468369] system 00:01: [io  0x0610] has been reserved
[    0.468379] system 00:01: [io  0x0800-0x080f] has been reserved
[    0.468389] system 00:01: [io  0x0400-0x047f] has been reserved
[    0.468400] system 00:01: [io  0x0500-0x053f] has been reserved
[    0.468412] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.468423] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.468434] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.468444] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.468455] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.468466] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.468477] system 00:01: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.468491] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.468537] pnp 00:02: [io  0x0000-0x001f]
[    0.468545] pnp 00:02: [io  0x0081-0x0091]
[    0.468553] pnp 00:02: [io  0x0093-0x009f]
[    0.468561] pnp 00:02: [io  0x00c0-0x00df]
[    0.468569] pnp 00:02: [dma 4]
[    0.468683] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.468784] pnp 00:03: [io  0x0070-0x0077]
[    0.468900] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.469145] pnp 00:04: [irq 0 disabled]
[    0.469173] pnp 00:04: [irq 8]
[    0.469182] pnp 00:04: [mem 0xfed00000-0xfed003ff]
[    0.469307] pnp 00:04: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.469353] pnp 00:05: [io  0x00f0]
[    0.469370] pnp 00:05: [irq 13]
[    0.469494] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.469538] pnp 00:06: [mem 0xff800000-0xffffffff]
[    0.469649] pnp 00:06: Plug and Play ACPI device, IDs INT0800 (active)
[    0.469715] pnp 00:07: [io  0x0060]
[    0.469724] pnp 00:07: [io  0x0064]
[    0.469742] pnp 00:07: [irq 1]
[    0.469872] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.469944] pnp 00:08: [irq 12]
[    0.470061] pnp 00:08: Plug and Play ACPI device, IDs PNP0f13 (active)
[    0.470360] pnp: PnP ACPI: found 9 devices
[    0.470367] ACPI: ACPI bus type pnp unregistered
[    0.470377] PnPBIOS: Disabled by ACPI PNP
[    0.513200] pci 0000:02:00.0: no compatible bridge window for [mem 0xfffe0000-0xffffffff pref]
[    0.513218] PCI: max bus depth: 1 pci_try_num: 2
[    0.513304] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.513317] pci 0000:00:1c.0:   bridge window [io  0x5000-0x5fff]
[    0.513332] pci 0000:00:1c.0:   bridge window [mem 0x37300000-0x383fffff]
[    0.513345] pci 0000:00:1c.0:   bridge window [mem 0x30000000-0x30ffffff 64bit pref]
[    0.513372] pci 0000:02:00.0: BAR 6: assigned [mem 0x31020000-0x3103ffff pref]
[    0.513382] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    0.513393] pci 0000:00:1c.1:   bridge window [io  0x3000-0x4fff]
[    0.513407] pci 0000:00:1c.1:   bridge window [mem 0x36300000-0x372fffff]
[    0.513420] pci 0000:00:1c.1:   bridge window [mem 0x31000000-0x320fffff 64bit pref]
[    0.513437] pci 0000:00:1c.2: PCI bridge to [bus 03-03]
[    0.513448] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    0.513462] pci 0000:00:1c.2:   bridge window [mem 0x35200000-0x362fffff]
[    0.513475] pci 0000:00:1c.2:   bridge window [mem 0x32100000-0x330fffff 64bit pref]
[    0.513492] pci 0000:00:1c.3: PCI bridge to [bus 04-04]
[    0.513502] pci 0000:00:1c.3:   bridge window [io  0x1000-0x1fff]
[    0.513517] pci 0000:00:1c.3:   bridge window [mem 0x34100000-0x351fffff]
[    0.513530] pci 0000:00:1c.3:   bridge window [mem 0x33100000-0x340fffff 64bit pref]
[    0.513547] pci 0000:00:1e.0: PCI bridge to [bus 05-05]
[    0.513616] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.513632] pci 0000:00:1c.0: setting latency timer to 64
[    0.513664] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.513677] pci 0000:00:1c.1: setting latency timer to 64
[    0.513707] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.513720] pci 0000:00:1c.2: setting latency timer to 64
[    0.513751] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.513763] pci 0000:00:1c.3: setting latency timer to 64
[    0.513782] pci 0000:00:1e.0: setting latency timer to 64
[    0.513795] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.513804] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.513813] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.513823] pci_bus 0000:00: resource 7 [mem 0x20000000-0xfebfffff]
[    0.513832] pci_bus 0000:01: resource 0 [io  0x5000-0x5fff]
[    0.513842] pci_bus 0000:01: resource 1 [mem 0x37300000-0x383fffff]
[    0.513852] pci_bus 0000:01: resource 2 [mem 0x30000000-0x30ffffff 64bit pref]
[    0.513861] pci_bus 0000:02: resource 0 [io  0x3000-0x4fff]
[    0.513871] pci_bus 0000:02: resource 1 [mem 0x36300000-0x372fffff]
[    0.513880] pci_bus 0000:02: resource 2 [mem 0x31000000-0x320fffff 64bit pref]
[    0.513890] pci_bus 0000:03: resource 0 [io  0x2000-0x2fff]
[    0.513900] pci_bus 0000:03: resource 1 [mem 0x35200000-0x362fffff]
[    0.513909] pci_bus 0000:03: resource 2 [mem 0x32100000-0x330fffff 64bit pref]
[    0.513919] pci_bus 0000:04: resource 0 [io  0x1000-0x1fff]
[    0.513929] pci_bus 0000:04: resource 1 [mem 0x34100000-0x351fffff]
[    0.513938] pci_bus 0000:04: resource 2 [mem 0x33100000-0x340fffff 64bit pref]
[    0.513949] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
[    0.513958] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff]
[    0.513967] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
[    0.513977] pci_bus 0000:05: resource 7 [mem 0x20000000-0xfebfffff]
[    0.514105] NET: Registered protocol family 2
[    0.514321] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.514999] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.515153] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.515299] TCP: Hash tables configured (established 16384 bind 16384)
[    0.515307] TCP reno registered
[    0.515316] UDP hash table entries: 256 (order: 1, 8192 bytes)
[    0.515333] UDP-Lite hash table entries: 256 (order: 1, 8192 bytes)
[    0.515575] NET: Registered protocol family 1
[    0.515629] pci 0000:00:02.0: Boot video device
[    0.515693] pci 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.515725] pci 0000:00:1d.0: PCI INT A disabled
[    0.515748] pci 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.515778] pci 0000:00:1d.1: PCI INT B disabled
[    0.515800] pci 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.515830] pci 0000:00:1d.2: PCI INT C disabled
[    0.515851] pci 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.515882] pci 0000:00:1d.3: PCI INT D disabled
[    0.515906] pci 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.516072] pci 0000:00:1d.7: PCI INT A disabled
[    0.516118] PCI: CLS 0 bytes, default 64
[    0.516132] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
[    0.516140] Simple Boot Flag at 0x44 set to 0x1
[    0.517431] audit: initializing netlink socket (disabled)
[    0.517461] type=2000 audit(1369737610.512:1): initialized
[    0.578593] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.586017] VFS: Disk quotas dquot_6.5.2
[    0.586246] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.588501] fuse init (API version 7.17)
[    0.588895] msgmni has been set to 928
[    0.590244] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.590377] io scheduler noop registered
[    0.590385] io scheduler deadline registered
[    0.590415] io scheduler cfq registered (default)
[    0.590838] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.590941] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.591134] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.591222] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.591398] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.591484] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    0.591646] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.591736] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X
[    0.592097] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.592193] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.592443] intel_idle: MWAIT substates: 0x20220
[    0.592459] intel_idle: v0.4 model 0x1C
[    0.592465] intel_idle: lapic_timer_reliable_states 0x2
[    0.592473] Marking TSC unstable due to TSC halts in idle states deeper than C2
[    0.593012] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.593415] ACPI: AC Adapter [ACAD] (on-line)
[    0.593772] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.593791] ACPI: Power Button [PWRB]
[    0.594186] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.594517] ACPI: Lid Switch [LID0]
[    0.594694] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.594709] ACPI: Sleep Button [SLPB]
[    0.594926] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.594942] ACPI: Power Button [PWRF]
[    0.598956] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.598994] ACPI: Battery Slot [BAT1] (battery absent)
[    0.599108] ERST: Table is not found!
[    0.599114] GHES: HEST is not enabled!
[    0.599494] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.599965] ACPI: Battery Slot [BAT1] (battery absent)
[    0.600074] isapnp: Scanning for PnP cards...
[    0.955330] isapnp: No Plug & Play device found
[    1.224346] Freeing initrd memory: 19644k freed
[    1.285467] Linux agpgart interface v0.103
[    1.285634] agpgart-intel 0000:00:00.0: Intel 945GME Chipset
[    1.285920] agpgart-intel 0000:00:00.0: detected gtt size: 262144K total, 262144K mappable
[    1.286162] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    1.286411] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x20000000
[    1.290906] brd: module loaded
[    1.293328] loop: module loaded
[    1.293748] ata_piix 0000:00:1f.2: version 2.13
[    1.293783] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.293795] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    1.293868] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.294687] scsi0 : ata_piix
[    1.294924] scsi1 : ata_piix
[    1.296607] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x60a0 irq 14
[    1.296615] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x60a8 irq 15
[    1.297857] Fixed MDIO Bus: probed
[    1.297925] tun: Universal TUN/TAP device driver, 1.6
[    1.297930] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.298107] PPP generic driver version 2.4.2
[    1.298421] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.298472] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.298512] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.298520] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.298656] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.298698] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    1.298718] ehci_hcd 0000:00:1d.7: debug port 1
[    1.302596] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    1.302638] ehci_hcd 0000:00:1d.7: irq 16, io mem 0x38544400
[    1.316038] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.316417] hub 1-0:1.0: USB hub found
[    1.316430] hub 1-0:1.0: 8 ports detected
[    1.316625] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.316666] uhci_hcd: USB Universal Host Controller Interface driver
[    1.316729] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.316749] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.316757] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.316916] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.316962] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00006080
[    1.317348] hub 2-0:1.0: USB hub found
[    1.317361] hub 2-0:1.0: 2 ports detected
[    1.317516] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.317534] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.317542] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.317683] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.317747] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00006060
[    1.318111] hub 3-0:1.0: USB hub found
[    1.318123] hub 3-0:1.0: 2 ports detected
[    1.318276] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.318294] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.318301] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.318434] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.318497] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00006040
[    1.318861] hub 4-0:1.0: USB hub found
[    1.318873] hub 4-0:1.0: 2 ports detected
[    1.319033] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.319051] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.319059] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.319206] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.319268] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00006020
[    1.319632] hub 5-0:1.0: USB hub found
[    1.319644] hub 5-0:1.0: 2 ports detected
[    1.319955] usbcore: registered new interface driver libusual
[    1.320109] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
[    1.321285] i8042: Warning: Keylock active
[    1.330546] i8042: Detected active multiplexing controller, rev 1.1
[    1.336531] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.336550] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.336638] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.336722] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.336799] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.337202] mousedev: PS/2 mouse device common for all mice
[    1.337785] rtc_cmos 00:03: RTC can wake from S4
[    1.338015] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.338066] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.338262] device-mapper: uevent: version 1.0.3
[    1.338477] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.338540] EISA: Probing bus 0 at eisa.0
[    1.338552] EISA: Cannot allocate resource for mainboard
[    1.338559] Cannot allocate resource for EISA slot 1
[    1.338565] Cannot allocate resource for EISA slot 2
[    1.338570] Cannot allocate resource for EISA slot 3
[    1.338576] Cannot allocate resource for EISA slot 4
[    1.338582] Cannot allocate resource for EISA slot 5
[    1.338587] Cannot allocate resource for EISA slot 6
[    1.338593] Cannot allocate resource for EISA slot 7
[    1.338599] Cannot allocate resource for EISA slot 8
[    1.338603] EISA: Detected 0 cards.
[    1.338623] cpufreq-nforce2: No nForce2 chipset.
[    1.338822] cpuidle: using governor ladder
[    1.339136] cpuidle: using governor menu
[    1.339142] EFI Variables Facility v0.08 2004-May-17
[    1.339785] TCP cubic registered
[    1.340144] NET: Registered protocol family 10
[    1.341685] NET: Registered protocol family 17
[    1.341699] Registering the dns_resolver key type
[    1.341748] Using IPI No-Shortcut mode
[    1.342113] PM: Hibernation image not present or could not be loaded.
[    1.342151] registered taskstats version 1
[    1.360189] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.361591]   Magic number: 13:290:680
[    1.361764] rtc_cmos 00:03: setting system clock to 2013-05-28 10:40:12 UTC (1369737612)
[    1.362538] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.362544] EDD information not available.
[    1.509069] ata1.00: ATA-8: ST9250315AS, 0001SDM1, max UDMA/133
[    1.509088] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.524791] ata1.00: configured for UDMA/133
[    1.525274] scsi 0:0:0:0: Direct-Access     ATA      ST9250315AS      0001 PQ: 0 ANSI: 5
[    1.525678] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.525792] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.525925] sd 0:0:0:0: [sda] Write Protect is off
[    1.525936] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.526074] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.573754]  sda: sda1 sda2 < sda5 >
[    1.574919] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.574988] Freeing unused kernel memory: 716k freed
[    1.575656] Write protecting the kernel text: 5636k
[    1.575753] Write protecting the kernel read-only data: 2332k
[    1.622170] udevd[90]: starting version 175
[    1.724209] [Firmware Bug]: battery: (dis)charge rate invalid.
[    1.740220] usb 1-5: new high-speed USB device number 3 using ehci_hcd
[    1.789922] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5
[    1.790097] ACPI: Video Device [OVGA] (multi-head: yes  rom: yes  post: no)
[    1.809049] [drm] Initialized drm 1.1.0 20060810
[    1.847915] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.847933] i915 0000:00:02.0: setting latency timer to 64
[    1.963720] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.963793] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.963864] r8169 0000:02:00.0: setting latency timer to 64
[    1.963978] r8169 0000:02:00.0: irq 44 for MSI/MSI-X
[    1.967778] wmi: Mapper loaded
[    1.972690] mtrr: no more MTRRs available
[    1.972701] [drm] MTRR allocation failed.  Graphics performance may suffer.
[    1.974096] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    1.974107] [drm] Driver supports precise vblank timestamp query.
[    1.983188] r8169 0000:02:00.0: eth0: RTL8102e at 0xdfd2c000, 00:23:8b:6e:b0:36, XID 04a00000 IRQ 44
[    2.032526] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    2.228122] usb 2-2: new full-speed USB device number 2 using uhci_hcd
[    2.352192] [drm] initialized overlay support
[    2.374433] fbcon: inteldrmfb (fb0) is primary device
[    2.374593] Console: switching to colour frame buffer device 128x37
[    2.374672] fb0: inteldrmfb frame buffer device
[    2.374678] drm: registered panic notifier
[    2.374722] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    2.429390] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input6
[    2.429911] generic-usb 0003:046D:C52F.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-2/input0
[    2.436824] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.1/input/input7
[    2.439805] generic-usb 0003:046D:C52F.0002: input,hiddev0,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-2/input1
[    2.440170] usbcore: registered new interface driver usbhid
[    2.440180] usbhid: USB HID core driver
[    3.085449] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    3.085459] EXT4-fs (sda1): write access will be enabled during recovery
[    3.712075] EXT4-fs (sda1): recovery complete
[    3.713405] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   18.934292] Adding 1455100k swap on /dev/sda5.  Priority:-1 extents:1 across:1455100k 
[   18.958859] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.001350] udevd[417]: starting version 175
[   19.132637] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   19.154206] lp: driver loaded but no devices found
[   19.826338] Bluetooth: Core ver 2.16
[   19.832068] NET: Registered protocol family 31
[   19.832080] Bluetooth: HCI device and connection manager initialized
[   19.832090] Bluetooth: HCI socket layer initialized
[   19.832098] Bluetooth: L2CAP socket layer initialized
[   19.832126] Bluetooth: SCO socket layer initialized
[   19.840478] ppdev: user-space parallel port driver
[   19.872787] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.872799] Bluetooth: BNEP filters: protocol multicast
[   19.909985] Bluetooth: RFCOMM TTY layer initialized
[   19.910004] Bluetooth: RFCOMM socket layer initialized
[   19.910013] Bluetooth: RFCOMM ver 1.11
[   19.998127] type=1400 audit(1369737631.132:2): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=659 comm="apparmor_parser"
[   20.000082] type=1400 audit(1369737631.136:3): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=659 comm="apparmor_parser"
[   20.216064] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.216214] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   20.216286] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   20.303196] cfg80211: Calling CRDA to update world regulatory domain
[   20.314138] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   20.314562] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   20.340825] type=1400 audit(1369737631.476:4): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=692 comm="apparmor_parser"
[   20.342514] type=1400 audit(1369737631.476:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=692 comm="apparmor_parser"
[   20.343488] type=1400 audit(1369737631.476:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=692 comm="apparmor_parser"
[   20.398417] ath5k 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   20.398446] ath5k 0000:03:00.0: setting latency timer to 64
[   20.398582] ath5k 0000:03:00.0: registered as 'phy0'
[   20.860229] intel_rng: FWH not detected
[   20.935908] ath: EEPROM regdomain: 0x65
[   20.935919] ath: EEPROM indicates we should expect a direct regpair map
[   20.935931] ath: Country alpha2 being used: 00
[   20.935937] ath: Regpair used: 0x65
[   20.935948] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   20.935961] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   20.935970] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   20.935982] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   20.935992] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   20.936204] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   20.936216] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   20.936227] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   20.936236] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   20.936247] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   20.936256] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   20.936267] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   20.936276] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   20.936287] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   20.936295] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   20.936307] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   20.936316] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   20.936327] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   20.936336] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   20.936347] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   20.936355] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   20.936367] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   20.936376] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   20.936386] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   20.936395] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   20.936406] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   20.936415] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   20.943080] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   20.944409] leds_ss4200: no LED devices found
[   20.969746] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   20.992763] Registered led device: ath5k-phy0::rx
[   20.992859] Registered led device: ath5k-phy0::tx
[   20.992896] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   21.068117] Linux video capture interface: v2.00
[   21.070590] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:62c0)
[   21.105334] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/input/input10
[   21.105839] usbcore: registered new interface driver uvcvideo
[   21.105849] USB Video Class driver (1.1.1)
[   21.685594] init: failsafe main process (784) killed by TERM signal
[   22.072253] psmouse serio2: synaptics: Touchpad model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04773/0xa40000/0xa0000
[   22.115371] type=1400 audit(1369737633.248:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=888 comm="apparmor_parser"
[   22.127219] type=1400 audit(1369737633.260:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=889 comm="apparmor_parser"
[   22.129050] type=1400 audit(1369737633.264:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=889 comm="apparmor_parser"
[   22.130005] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input11
[   22.133980] type=1400 audit(1369737633.268:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=889 comm="apparmor_parser"
[   22.200689] type=1400 audit(1369737633.336:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=908 comm="apparmor_parser"
[   22.225714] r8169 0000:02:00.0: eth0: link down
[   22.228335] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.236415] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.266397] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.267913] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.510330] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   22.510344] cfg80211: World regulatory domain updated:
[   22.510352] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   22.510364] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.510375] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   22.510385] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   22.510396] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.510406] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.277518] init: gdm main process (1055) killed by TERM signal
[   24.126226] init: plymouth-stop pre-start process (1226) terminated with status 1
[  273.324500] r8169 0000:02:00.0: eth0: link up
[  273.324759] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  289.920050] eth0: no IPv6 routers present
[  765.762078] r8169 0000:02:00.0: eth0: link down
[  770.316788] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  896.497888] r8169 0000:02:00.0: eth0: link up
[  896.498062] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  913.856076] eth0: no IPv6 routers present
[ 1439.661996] r8169 0000:02:00.0: eth0: link down
[ 1444.267017] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1455.692812] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1536.646077] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1536.647500] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1537.591779] r8169 0000:02:00.0: eth0: link down
[ 1537.591927] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1537.593344] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1537.614161] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1559.651843] r8169 0000:02:00.0: eth0: link up
[ 1559.652113] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1570.600106] eth0: no IPv6 routers present
[ 1777.489475] r8169 0000:02:00.0: eth0: link down
[ 1782.252646] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1828.601158] r8169 0000:02:00.0: eth0: link up
[ 1828.601353] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1839.048113] eth0: no IPv6 routers present
```

```
$ sudo lshw -C network
[sudo] password for welcome: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:23:8b:6e:b0:36
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.1.15 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:44 ioport:3000(size=256) memory:31010000-31010fff memory:31000000-3100ffff memory:31020000-3103ffff
  *-network DISABLED
       description: Wireless interface
       product: AR242x / AR542x Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:23:4d:00:b8:f6
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=3.2.0-44-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:35200000-3520ffff
```

```
$ iwlist scan
lo        Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

eth0      Interface doesn't support scanning.
```

```
$ iwlist scan wlan0
iwlist: unknown command `wlan0' (check 'iwlist --help').
```

```
$ lsb_release -d
Description:    Ubuntu 12.04.2 LTS
```

```
$ uname -mr
3.2.0-44-generic i686
```

```
$ sudo /etc/init.d/networking restart
[sudo] password for welcome: 
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces... 

```

---

### Post by PDA1 on 2013-05-28
Note- If I shut the computer down and remove all power from it (AC and battery) then re-boot- the Wireless connection panel/icon lists my wireless connection (router) and indicates that it's connected to my computer. But, still can't access the web through Firefox.

---

### Post by Karlchen on 2013-05-28
Hello, PDA1.

Your problem may be much less serious than you think. :)
Unlike Windows 7 e.g. where you can connect to network A using your wired network card and to network B using your WLAN card simultaneously, the Ubuntu Network Manager by default uses either the wired network, if connected, or the WLAN card, if the wired card is not connected.
So, simply pull the wired ethernet cable and wait a few seconds. Network Manager should come up and tell you that WLAN connections are availabe.
Select your router, enter the password and the connection to the router should be established.
This works fine here on several netbooks / notebooks which run Ubuntu 12.04.2.

Kind regards,
Karl

---

### Post by PDA1 on 2013-05-28
Already tried that.

Doesn't work.

Read my comment just above yours.

---

### Post by steeldriver on 2013-05-28
The ath5k driver sometimes falls on its face with hardware encryption - try

```

sudo modprobe -rf ath5k

sudo modprobe -v ath5k nohwcrypt=Y

```

If that helps, we can write a config file to make the change persistent

---

### Post by PDA1 on 2013-05-28
No success. 

Here are the results of the commands you recommended;

```
welcome@welcome-laptop:~$ sudo modprobe -rf ath5k
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
welcome@welcome-laptop:~$ 
welcome@welcome-laptop:~$ sudo modprobe -v ath5k nohwcrypt=Y
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
insmod /lib/modules/3.2.0-44-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.2.0-44-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.2.0-44-generic/kernel/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/3.2.0-44-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko nohwcrypt=Y


```

---

### Post by PDA1 on 2013-05-28
The problem has sort of been fixed. 

Don't ask me how I did it...I have no clear idea.

What I did was to install ndiswrapper.

Then, I deleted the wireless connection I connect to.

Then, added the connection back in.

Pretty amazing isn't it?!

I have the utmost confidence that there will be problems in the next few hours concerning this wireless connection stuff.

---

### Post by PDA1 on 2013-05-28
Figures, I spoke too soon.

When I put the computer in "Suspend" then I can't get a wireless connection to start. No wireless connection appears (in my case it's "PA7V5". 

The wireless icon is completely grayed out.

As before, when I shut the computer down, remove all power from it and the reboot the wireless connection reappears and all is well.

Any ideas?

---

### Post by Karlchen on 2013-05-28
> **PDA1 said:**
> Already tried that.
Doesn't work.
Read my comment just above yours. No, it was not clear that you might have tried what I suggested.
You talked about removing the AC power cable.
I gave the advice of pulling the ethernet cable from the wired network card in order to make sure that Network Manager switches to using the wifi adapter.
You have written nothing that suggests you may have tried this.

---

### Post by Karlchen on 2013-05-28
Answers to detail questions / problems mentioned in the initial post:
[quote="PDA1"]$ lsmod | grep wlan0
  The command was supposed to be $ lsmod | grep "wlan_module_name", 
but since I have no idea what they're talking about in the BEFORE YOUR POST
topic I have no idea what to enter here.[/quote]
The command should read ```
lsmod | grep ath5k
``` in your case, because your wifi adapter uses the driver ath5k.
[quote="PDA1"]sudo /etc/init.d/networking restart[/quote] The commandlines should be ```
sudo service network-manager stop
sudo service network-manager start
```instead.
[quote="PDA1"]$ lspci -nn | grep AR542x
 03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)[/quote]
The command should read ```
sudo lspci -vnn -s 03:00.0
``` in your case in order to give more detailled screen output.
(Won't solve your problem, but should be mentioned.)

---

### Post by Karlchen on 2013-05-28
Hello, PDA1.

Switched to the only machine here which has got an Atheros wifi adapter and which runs Ubuntu 12.04.2 32-bit, hm, some might call it Mint 13 xfce desktop. Yet, as the difference between genuine Ubuntu and genuine Mint is merely the desktop, this does not really matter.
```
uname -a; lsb_release -rd; cat /etc/os-release
Linux unimatrix0 3.2.0-44-generic #69-Ubuntu SMP Thu May 16 18:27:54 UTC 2013 i686 i686 i386 GNU/Linux
Description:    Linux Mint 13 Maya
Release:    13
NAME="Ubuntu"
VERSION="12.04.2 LTS, Precise Pangolin"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu precise (12.04.2 LTS)"
VERSION_ID="12.04"
```

[B][U](1) Stage 1 - connection using the wired adapter
[/U][/B]
[U]The network interfaces:
[/U]Extract from the commandline "[inxi -Fx]("http://www.webupd8.org/2009/11/shell-system-information-tool-for-linux.html")": ```
Network:   Card-1: Atheros AR9285 Wireless Network Adapter (PCI-Express) driver: ath9k bus-ID: 04:00.0
           IF: wlan0 state: down mac: 00:25:d3:eb:5e:c8
           Card-2: NVIDIA MCP79 Ethernet driver: forcedeth port: d080 bus-ID: 00:0a.0
           IF: eth0 state: up speed: 100 Mbps duplex: full mac: 00:01:2e:2b:26:c2
```
As can be seen the wifi adapater "wlan0" is down. The wired adapter "eth0" is up.

_The established network connections:_
```
ifconfig
eth0      Link encap:Ethernet  Hardware Adresse 00:01:2e:2b:26:c2  
          inet Adresse:192.168.178.25  Bcast:192.168.178.255  Maske:255.255.255.0
          inet6-Adresse: fe80::201:2eff:fe2b:26c2/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:2137 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1888 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX-Bytes:2285528 (2.2 MB)  TX-Bytes:286264 (286.2 KB)
          Interrupt:21 Basisadresse:0xe000 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:220 errors:0 dropped:0 overruns:0 frame:0
          TX packets:220 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX-Bytes:18696 (18.6 KB)  TX-Bytes:18696 (18.6 KB)

wlan0     Link encap:Ethernet  Hardware Adresse 00:25:d3:eb:5e:c8  
          inet6-Adresse: fe80::225:d3ff:feeb:5ec8/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:108 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX-Bytes:20739 (20.7 KB)  TX-Bytes:10830 (10.8 KB)
```
Only the wired adapter "eth0" has been assigned an IPv4 address. The wifi adapter "wlan0" has got no IPv4 address. - IPv6 is not in use here.

```
iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.
``` This confirms that wlan0 is not in use.


[B][U](2) Swapping the active network adapter
[/U][/B]
_Next steps:_
Now the network cable will be pulled. So the connection to my router and to this page will be lost for a short time.
A few seconds later the WLAN connection should be established and the connection to this page, too. (May have to login again.)
Will then finish this post ...
Aft pulling the ethernet cable, had to click the grayed out network icon in the systray area and click on my router SSID in order to convince Network Manager to establish the connection to it.
Had to click refresh only in this page in order to be back in the post.


[B][U](3) Stage 2 - connection using the wireless Atheros adapter
[/U][/B]

[U]The network interfaces (revisited):
[/U]Extract from the commandline "[inxi -Fx]("http://www.webupd8.org/2009/11/shell-system-information-tool-for-linux.html")": ```
Network:   Card-1: Atheros AR9285 Wireless Network Adapter (PCI-Express) driver: ath9k bus-ID: 04:00.0
           IF: wlan0 state: up mac: 00:25:d3:eb:5e:c8
           Card-2: NVIDIA MCP79 Ethernet driver: forcedeth port: d080 bus-ID: 00:0a.0
           IF: eth0 state: down mac: 00:01:2e:2b:26:c2
```
As can be seen the wifi adapater "wlan0" is up now. The wired adapter "eth0" is down.

_The established network connections (revisited):_
```
ifconfig
eth0      Link encap:Ethernet  Hardware Adresse 00:01:2e:2b:26:c2  
          inet6-Adresse: fe80::201:2eff:fe2b:26c2/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:3169 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2663 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX-Bytes:3230982 (3.2 MB)  TX-Bytes:603686 (603.6 KB)
          Interrupt:21 Basisadresse:0xe000 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:320 errors:0 dropped:0 overruns:0 frame:0
          TX packets:320 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX-Bytes:26287 (26.2 KB)  TX-Bytes:26287 (26.2 KB)

wlan0     Link encap:Ethernet  Hardware Adresse 00:25:d3:eb:5e:c8  
          inet Adresse:192.168.178.22  Bcast:192.168.178.255  Maske:255.255.255.0
          inet6-Adresse: fe80::225:d3ff:feeb:5ec8/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:718 errors:0 dropped:0 overruns:0 frame:0
          TX packets:718 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX-Bytes:411820 (411.8 KB)  TX-Bytes:247041 (247.0 KB)
```
Now the  wifi adapter "wlan0" has got the IPv4 address. The wird adapter "eth0" has lost its IPv4 address.

```
 iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"FritzBox"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: C1:26:07:5F:EE:E1   
          Bit Rate=150 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:100   Missed beacon:0

eth0      no wireless extensions.
``` This confirms that wlan0 is now in use.


[B][U](4) Controlling system activities

[/U][/B]Of course, the system writes activities related to the network adapters to a log file: /var/log/syslog.
The following grep command will extract all lines created by the Network Manager from that file: ```
grep "NetworkManager" /var/log/syslog
``` Beware:
There may be quite a few messages related to Network Manager, in particular something does not work correctly.

This grep command will extract all lines directly related to my wifi adapter "ath9k" from syslog: ```
grep "ath9k" /var/log/syslog
```
```
grep "ath9k" /var/log/syslog
May 29 02:11:21 unimatrix0 kernel: [   13.083184] ath9k 0000:04:00.0: PCI INT A -> Link[LN3A] -> GSI 19 (level, low) -> IRQ 19
May 29 02:11:21 unimatrix0 kernel: [   13.083209] ath9k 0000:04:00.0: setting latency timer to 64
May 29 02:11:21 unimatrix0 kernel: [   13.689218] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
May 29 02:11:21 unimatrix0 kernel: [   13.691139] Registered led device: ath9k-phy0
May 29 02:11:36 unimatrix0 NetworkManager[967]: <info> (wlan0): new 802.11 WiFi device (driver: 'ath9k' ifindex: 3)
```
As your system uses the driver "ath5k" the corresponding command would be ```
grep "ath5k" /var/log/syslog
```

In short words,  you may wish to check your /var/log/syslog for lines related to
+ ath5k
+ NetworkManager
+ cfg80211 (might be worth, too)
and check why Network Manager may not be able to activate your wifi adapter or - telling from your reports - rather why it will de-activate the adapter or which other problems are logged in syslog relating to ath5k.


[B][U](5) Useful commands to inspect hardware
[/U][/B]
Some of them have been used in your initial post already, just wished to give them as a concise list here.

[LIST]
[*]```
sudo lshw -c  network
``` In the output section about your wifi adapter there will be a line specifying "bus information", on my machine e.g. "Bus-Informationen: pci@0000:04:00.0". The number string after the "pci@" will be fed to the next command. 
[*]If I remember right the needed string on your system is "03:00.0". So for you the command will be ```
sudo lspci -vnn -s 03:00.0
``` and yield output similar to the one generated on my machine by running ```
sudo lspci -vnn -s 04:00.0
04:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: AzureWave AW-NE785 / AW-NE785H 802.11bgn Wireless Full or Half-size Mini PCIe Card [1a3b:1089]
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at febf0000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [60] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 00-15-17-ff-ff-24-14-12
    Capabilities: [170] Power Budgeting <?>
    Kernel driver in use: ath9k
    Kernel modules: ath9k
``` 
[*]```
rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
``` displays that the wifi adapter is neither soft blocked, nor hard blocked. 
[*]```
ifconfig
``` 
[*]```
iwconfig
``` 
[*]```
inxi -Fx
``` will display a concise summary of your system hard- and software environment. Although **inxi** is not available on genuine Ubuntu by default, it can be got, installed and used on genuine Ubuntu without much hassle: **[inxi]("http://www.webupd8.org/2009/11/shell-system-information-tool-for-linux.html")**. 
[/LIST]


Kind regards,
Karl

---

### Post by Karlchen on 2013-05-29
Hello, PDA1.

Performing some searches for "Ubuntu 12.04 Atheros AR2425" in the Ubuntu and Mint forums and on Google leads me to the conclusion that the difference between your system - wifi adapter not functioning properly - and mine - wifi adapter functioning reliably - really is the difference between Atheros AR2425 (yours) and Atheros AR9285 (mine).

Maybe this Ubuntu Forum thread will be help you: [B][Atheros "ath5k" Wireless Not Working]("http://ubuntuforums.org/showthread.php?t=1776004")[URL="http://ubuntuforums.org/showthread.php?t=1776004"]
[/URL][/B]
Kind regards,
Karl[B][URL="http://ubuntuforums.org/showthread.php?t=1776004"]
[/URL][/B]

---

