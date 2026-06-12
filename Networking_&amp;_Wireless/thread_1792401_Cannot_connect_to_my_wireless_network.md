---
title: "Cannot connect to my wireless network"
date: 2011-06-28
forum: Networking &amp; Wireless
---

### Post by SoVW on 2011-06-28
I upgraded to Ubuntu 11.04 from 10.10 a couple of days ago and now I cannot connect to my wireless network. I can see all the networks and I managed to connect to something called BTopenzone, just to see if I could connect to anything, and that worked. I also run windows 7 on the same computer and setup and it connects fine to my wireless network. Before I installed the Ubuntu upgrade I could connect without any problems. I've had a look at the settings for the connection in Ubuntu but I don't understand them. 

My router is a dlink dir-655

My receiver is a edimax ew-7711uan wireless usb adapter

Any suggestions as to why it's not working?

Thanks SoVW

---

### Post by SoVW on 2011-06-28
Just read the sticky.

HTH


2) Wireless brand, model and wireless chipset



$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.5 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 06)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
02:00.0 IDE interface: VIA Technologies, Inc. VT6415 PATA IDE Host Controller





$ lsusb
Bus 002 Device 005: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 004: ID 0bc2:5071 Seagate RSS LLC
Bus 002 Device 003: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 7392:7711 Edimax Technology Co., Ltd EW-7711UTn nLite Wireless Adapter [Ralink RT2870]
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub






3) Check interface




$ ifconfig
eth0      Link encap:Ethernet  HWaddr 20:cf:30:6f:be:1d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:40

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1f:1f:e3:50:1c  
          inet6 addr: fe80::21f:1fff:fee3:501c/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1360 (1.3 KB)  TX bytes:2460 (2.4 KB)








$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on




4) Check for modules



$ lsmod
Module                  Size  Used by
cryptd                 19801  0
aes_i586               16956  0
aes_generic            38023  1 aes_i586
binfmt_misc            13213  1
snd_hda_codec_hdmi     27479  1
snd_hda_codec_realtek   255820  1
snd_hda_intel          24140  2
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
rt2870sta             410104  0
snd_hwdep              13274  1 snd_hda_codec
arc4                   12473  2
snd_pcm                80244  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
rt2800usb              17907  0
rt2800lib              43824  1 rt2800usb
crc_ccitt              12595  2 rt2870sta,rt2800lib
rt2x00usb              19693  1 rt2800usb
rt2x00lib              39075  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              257001  3 rt2800lib,rt2x00usb,rt2x00lib
i915                  450979  3
snd_timer              28659  2 snd_pcm,snd_seq
ipt_REJECT             12512  1
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
ipt_LOG                12784  5
xt_limit               12541  7
joydev                 17322  0
xt_tcpudp              12531  8
ppdev                  12849  0
ipt_addrtype           12535  4
cfg80211              156212  2 rt2x00lib,mac80211
xt_state               12514  7
drm_kms_helper         40745  1 i915
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                59039  0
ip6table_filter        12711  1
ip6_tables             22545  1 ip6table_filter
nf_nat_irc             12542  0
nf_conntrack_irc       13138  1 nf_nat_irc
drm                   184133  4 i915,drm_kms_helper
nf_nat_ftp             12548  0
nf_nat                 24827  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      19024  9 nf_nat
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
soundcore              12600  1 snd
nf_conntrack_ftp       13106  1 nf_nat_ftp
serio_raw              12990  0
nf_conntrack           69744  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
iptable_filter         12706  1
ip_tables              18125  1 iptable_filter
x_tables               21907  10 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
parport_pc             32111  1
asus_atk0110           17664  0
lp                     13349  0
parport                36746  3 ppdev,parport_pc,lp
usb_storage            43946  1
usbhid                 41704  0
uas                    17676  0
hid                    77084  1 usbhid
r8169                  46630  0
pata_via               13368  0





5) Kernal boot messages





$dmesg
[    0.335731] AppArmor: AppArmor Filesystem Enabled
[    0.335757] pnp: PnP ACPI init
[    0.335772] ACPI: bus type pnp registered
[    0.335878] pnp 00:00: [bus 00-ff]
[    0.335880] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.335882] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.335884] pnp 00:00: [io  0x0d00-0xffff window]
[    0.335885] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.335887] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.335889] pnp 00:00: [mem 0xe0000000-0xf7ffffff window]
[    0.335890] pnp 00:00: [mem 0xfc000000-0xfed8ffff window]
[    0.335949] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.335957] pnp 00:01: [mem 0xfed14000-0xfed19fff]
[    0.335996] system 00:01: [mem 0xfed14000-0xfed19fff] has been reserved
[    0.335999] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.336025] pnp 00:02: [dma 4]
[    0.336027] pnp 00:02: [io  0x0000-0x000f]
[    0.336028] pnp 00:02: [io  0x0081-0x0083]
[    0.336030] pnp 00:02: [io  0x0087]
[    0.336031] pnp 00:02: [io  0x0089-0x008b]
[    0.336032] pnp 00:02: [io  0x008f]
[    0.336034] pnp 00:02: [io  0x00c0-0x00df]
[    0.336057] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.336065] pnp 00:03: [io  0x0070-0x0071]
[    0.336075] pnp 00:03: [irq 8]
[    0.336096] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.336102] pnp 00:04: [io  0x0061]
[    0.336122] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.336129] pnp 00:05: [io  0x00f0-0x00ff]
[    0.336133] pnp 00:05: [irq 13]
[    0.336155] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.336295] pnp 00:06: [io  0x0000-0xffffffffffffffff disabled]
[    0.336297] pnp 00:06: [io  0x0000-0xffffffffffffffff disabled]
[    0.336299] pnp 00:06: [io  0x0290-0x029f]
[    0.336332] system 00:06: [io  0x0290-0x029f] has been reserved
[    0.336335] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.336443] pnp 00:07: [io  0x0010-0x001f]
[    0.336445] pnp 00:07: [io  0x0022-0x003f]
[    0.336446] pnp 00:07: [io  0x0044-0x004d]
[    0.336448] pnp 00:07: [io  0x0050-0x005f]
[    0.336449] pnp 00:07: [io  0x0062-0x0063]
[    0.336450] pnp 00:07: [io  0x0065-0x006f]
[    0.336452] pnp 00:07: [io  0x0072-0x007f]
[    0.336453] pnp 00:07: [io  0x0080]
[    0.336455] pnp 00:07: [io  0x0084-0x0086]
[    0.336456] pnp 00:07: [io  0x0088]
[    0.336457] pnp 00:07: [io  0x008c-0x008e]
[    0.336459] pnp 00:07: [io  0x0090-0x009f]
[    0.336460] pnp 00:07: [io  0x00a2-0x00bf]
[    0.336462] pnp 00:07: [io  0x00e0-0x00ef]
[    0.336463] pnp 00:07: [io  0x04d0-0x04d1]
[    0.336465] pnp 00:07: [io  0x0800-0x087f]
[    0.336466] pnp 00:07: [io  0x0400-0x03ff disabled]
[    0.336468] pnp 00:07: [io  0x0500-0x057f]
[    0.336469] pnp 00:07: [io  0x0000-0xffffffffffffffff disabled]
[    0.336471] pnp 00:07: [mem 0xfed1c000-0xfed1ffff]
[    0.336473] pnp 00:07: [mem 0xfed20000-0xfed3ffff]
[    0.336474] pnp 00:07: [mem 0xfed40000-0xfed8ffff]
[    0.336524] system 00:07: [io  0x04d0-0x04d1] has been reserved
[    0.336526] system 00:07: [io  0x0800-0x087f] has been reserved
[    0.336528] system 00:07: [io  0x0500-0x057f] has been reserved
[    0.336530] system 00:07: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.336532] system 00:07: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.336534] system 00:07: [mem 0xfed40000-0xfed8ffff] has been reserved
[    0.336537] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.336587] pnp 00:08: [mem 0xfed00000-0xfed003ff]
[    0.336611] pnp 00:08: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.336798] pnp 00:09: [io  0x03f8-0x03ff]
[    0.336804] pnp 00:09: [irq 4]
[    0.336806] pnp 00:09: [dma 0 disabled]
[    0.336858] pnp 00:09: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.336919] pnp 00:0a: [io  0x0060]
[    0.336921] pnp 00:0a: [io  0x0064]
[    0.336922] pnp 00:0a: [mem 0xfec00000-0xfec00fff]
[    0.336924] pnp 00:0a: [mem 0xfee00000-0xfee00fff]
[    0.336958] system 00:0a: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.336960] system 00:0a: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.336963] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.337225] pnp 00:0b: [io  0x0378-0x037f]
[    0.337230] pnp 00:0b: [irq 7]
[    0.337231] pnp 00:0b: [dma 0 disabled]
[    0.337333] pnp 00:0b: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.337380] pnp 00:0c: [mem 0xf8000000-0xfbffffff]
[    0.337416] system 00:0c: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.337418] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.337582] pnp 00:0d: [mem 0x00000000-0x0009ffff]
[    0.337583] pnp 00:0d: [mem 0x000c0000-0x000cffff]
[    0.337585] pnp 00:0d: [mem 0x000e0000-0x000fffff]
[    0.337586] pnp 00:0d: [mem 0x00100000-0xdfffffff]
[    0.337588] pnp 00:0d: [mem 0xfed90000-0xffffffff]
[    0.337633] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.337635] system 00:0d: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.337637] system 00:0d: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.337639] system 00:0d: [mem 0x00100000-0xdfffffff] could not be reserved
[    0.337641] system 00:0d: [mem 0xfed90000-0xffffffff] could not be reserved
[    0.337644] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.337745] pnp: PnP ACPI: found 14 devices
[    0.337746] ACPI: ACPI bus type pnp unregistered
[    0.337749] PnPBIOS: Disabled by ACPI PNP
[    0.373470] pci 0000:00:1c.0: BAR 14: assigned [mem 0xf0000000-0xf01fffff]
[    0.373475] pci 0000:00:1c.0: BAR 15: assigned [mem 0xf0200000-0xf03fffff 64bit pref]
[    0.373478] pci 0000:00:1c.1: BAR 15: assigned [mem 0xf0400000-0xf05fffff 64bit pref]
[    0.373481] pci 0000:00:1c.4: BAR 14: assigned [mem 0xf0600000-0xf09fffff]
[    0.373483] pci 0000:00:1c.0: BAR 13: assigned [io  0x1000-0x1fff]
[    0.373485] pci 0000:00:1c.0: PCI bridge to [bus 03-03]
[    0.373488] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
[    0.373492] pci 0000:00:1c.0:   bridge window [mem 0xf0000000-0xf01fffff]
[    0.373495] pci 0000:00:1c.0:   bridge window [mem 0xf0200000-0xf03fffff 64bit pref]
[    0.373500] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    0.373503] pci 0000:00:1c.1:   bridge window [io  0xe000-0xefff]
[    0.373507] pci 0000:00:1c.1:   bridge window [mem 0xf7f00000-0xf7ffffff]
[    0.373510] pci 0000:00:1c.1:   bridge window [mem 0xf0400000-0xf05fffff 64bit pref]
[    0.373515] pci 0000:00:1c.4: PCI bridge to [bus 01-01]
[    0.373517] pci 0000:00:1c.4:   bridge window [io  0xd000-0xdfff]
[    0.373521] pci 0000:00:1c.4:   bridge window [mem 0xf0600000-0xf09fffff]
[    0.373525] pci 0000:00:1c.4:   bridge window [mem 0xf6f00000-0xf6ffffff 64bit pref]
[    0.373530] pci 0000:00:1e.0: PCI bridge to [bus 04-04]
[    0.373531] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.373535] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.373538] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.373547] pci 0000:00:1c.0: enabling device (0104 -> 0107)
[    0.373564] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.373568] pci 0000:00:1c.0: setting latency timer to 64
[    0.373577] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.373580] pci 0000:00:1c.1: setting latency timer to 64
[    0.373585] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.373588] pci 0000:00:1c.4: setting latency timer to 64
[    0.373594] pci 0000:00:1e.0: setting latency timer to 64
[    0.373597] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.373599] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.373601] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.373602] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.373604] pci_bus 0000:00: resource 8 [mem 0xe0000000-0xf7ffffff]
[    0.373606] pci_bus 0000:00: resource 9 [mem 0xfc000000-0xfed8ffff]
[    0.373608] pci_bus 0000:03: resource 0 [io  0x1000-0x1fff]
[    0.373609] pci_bus 0000:03: resource 1 [mem 0xf0000000-0xf01fffff]
[    0.373611] pci_bus 0000:03: resource 2 [mem 0xf0200000-0xf03fffff 64bit pref]
[    0.373613] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.373615] pci_bus 0000:02: resource 1 [mem 0xf7f00000-0xf7ffffff]
[    0.373617] pci_bus 0000:02: resource 2 [mem 0xf0400000-0xf05fffff 64bit pref]
[    0.373619] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.373620] pci_bus 0000:01: resource 1 [mem 0xf0600000-0xf09fffff]
[    0.373622] pci_bus 0000:01: resource 2 [mem 0xf6f00000-0xf6ffffff 64bit pref]
[    0.373624] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    0.373626] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    0.373628] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    0.373629] pci_bus 0000:04: resource 7 [mem 0x000d0000-0x000dffff]
[    0.373631] pci_bus 0000:04: resource 8 [mem 0xe0000000-0xf7ffffff]
[    0.373633] pci_bus 0000:04: resource 9 [mem 0xfc000000-0xfed8ffff]
[    0.373664] NET: Registered protocol family 2
[    0.373717] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.373867] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.374405] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.374667] TCP: Hash tables configured (established 131072 bind 65536)
[    0.374669] TCP reno registered
[    0.374671] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.374679] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.374754] NET: Registered protocol family 1
[    0.374764] pci 0000:00:02.0: Boot video device
[    0.374816] PCI: CLS 32 bytes, default 64
[    0.374976] cpufreq-nforce2: No nForce2 chipset.
[    0.375068] audit: initializing netlink socket (disabled)
[    0.375075] type=2000 audit(1309258796.236:1): initialized
[    0.383147] highmem bounce pool size: 64 pages
[    0.383152] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.384381] VFS: Disk quotas dquot_6.5.2
[    0.384427] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.384917] fuse init (API version 7.16)
[    0.384982] msgmni has been set to 1568
[    0.385155] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.385174] io scheduler noop registered
[    0.385176] io scheduler deadline registered
[    0.385187] io scheduler cfq registered (default)
[    0.385367] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.385388] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.385434] intel_idle: MWAIT substates: 0x1120
[    0.385436] intel_idle: v0.4 model 0x25
[    0.385437] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.385523] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.385527] ACPI: Power Button [PWRB]
[    0.385560] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.385563] ACPI: Power Button [PWRF]
[    0.385720] ACPI: acpi_idle yielding to intel_idle
[    0.387196] ERST: Table is not found!
[    0.387256] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.407608] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.407721] isapnp: Scanning for PnP cards...
[    0.528558] Freeing initrd memory: 12460k freed
[    0.760423] isapnp: No Plug & Play device found
[    0.783346] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.783608] Linux agpgart interface v0.103
[    0.783674] agpgart-intel 0000:00:00.0: Intel HD Graphics Chipset
[    0.783728] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    0.784592] agpgart-intel 0000:00:00.0: detected 32768K stolen memory
[    0.784712] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[    0.785611] brd: module loaded
[    0.786050] loop: module loaded
[    0.786127] i2c-core: driver [adp5520] using legacy suspend method
[    0.786129] i2c-core: driver [adp5520] using legacy resume method
[    0.786231] ata_piix 0000:00:1f.2: version 2.13
[    0.786254] ata_piix 0000:00:1f.2: PCI INT D -> GSI 21 (level, low) -> IRQ 21
[    0.786258] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.786289] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.786522] scsi0 : ata_piix
[    0.786595] scsi1 : ata_piix
[    0.787609] ata1: SATA max UDMA/133 cmd 0xb880 ctl 0xb800 bmdma 0xb080 irq 21
[    0.787614] ata2: SATA max UDMA/133 cmd 0xb480 ctl 0xb400 bmdma 0xb088 irq 21
[    0.787633] ata_piix 0000:00:1f.5: PCI INT D -> GSI 21 (level, low) -> IRQ 21
[    0.787637] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    0.787660] ata_piix 0000:00:1f.5: setting latency timer to 64
[    0.787806] scsi2 : ata_piix
[    0.787854] scsi3 : ata_piix
[    0.788586] ata3: SATA max UDMA/133 cmd 0xc880 ctl 0xc800 bmdma 0xc080 irq 21
[    0.788589] ata4: SATA max UDMA/133 cmd 0xc480 ctl 0xc400 bmdma 0xc088 irq 21
[    0.788635] pata_acpi 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.788653] pata_acpi 0000:02:00.0: setting latency timer to 64
[    0.788665] pata_acpi 0000:02:00.0: PCI INT A disabled
[    0.788883] Fixed MDIO Bus: probed
[    0.788904] PPP generic driver version 2.4.2
[    0.788934] tun: Universal TUN/TAP device driver, 1.6
[    0.788935] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.788998] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.789010] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.789022] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.789025] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    0.789055] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.789094] ehci_hcd 0000:00:1a.0: debug port 2
[    0.792977] ehci_hcd 0000:00:1a.0: cache line size of 32 is not supported
[    0.792989] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf7ef6000
[    0.805852] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.805990] hub 1-0:1.0: USB hub found
[    0.805993] hub 1-0:1.0: 2 ports detected
[    0.806051] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.806061] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.806064] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    0.806092] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.806125] ehci_hcd 0000:00:1d.0: debug port 2
[    0.810014] ehci_hcd 0000:00:1d.0: cache line size of 32 is not supported
[    0.810026] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf7ef5000
[    0.825826] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.825948] hub 2-0:1.0: USB hub found
[    0.825951] hub 2-0:1.0: 2 ports detected
[    0.825994] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.826002] uhci_hcd: USB Universal Host Controller Interface driver
[    0.826063] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.828852] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.828857] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.828943] mousedev: PS/2 mouse device common for all mice
[    0.829034] rtc_cmos 00:03: RTC can wake from S4
[    0.829893] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.829923] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.829982] device-mapper: uevent: version 1.0.3
[    0.830038] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: [email]dm-devel@redhat.com[/email]
[    0.830077] device-mapper: multipath: version 1.2.0 loaded
[    0.830079] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.830130] EISA: Probing bus 0 at eisa.0
[    0.830132] EISA: Cannot allocate resource for mainboard
[    0.830134] Cannot allocate resource for EISA slot 1
[    0.830135] Cannot allocate resource for EISA slot 2
[    0.830136] Cannot allocate resource for EISA slot 3
[    0.830138] Cannot allocate resource for EISA slot 4
[    0.830139] Cannot allocate resource for EISA slot 5
[    0.830140] Cannot allocate resource for EISA slot 6
[    0.830141] Cannot allocate resource for EISA slot 7
[    0.830143] Cannot allocate resource for EISA slot 8
[    0.830144] EISA: Detected 0 cards.
[    0.830221] cpuidle: using governor ladder
[    0.830281] cpuidle: using governor menu
[    0.830463] TCP cubic registered
[    0.830556] NET: Registered protocol family 10
[    0.830944] NET: Registered protocol family 17
[    0.830955] Registering the dns_resolver key type
[    0.831612] Using IPI No-Shortcut mode
[    0.831675] PM: Hibernation image not present or could not be loaded.
[    0.831684] registered taskstats version 1
[    0.831898]   Magic number: 15:605:983
[    0.832015] rtc_cmos 00:03: setting system clock to 2011-06-28 10:59:57 UTC (1309258797)
[    0.832018] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.832019] EDD information not available.
[    1.116193] ata3: SATA link down (SStatus 0 SControl 300)
[    1.126881] ata4: SATA link down (SStatus 0 SControl 300)
[    1.126932] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.258098] hub 1-1:1.0: USB hub found
[    1.258307] hub 1-1:1.0: 6 ports detected
[    1.369252] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    1.373235] Refined TSC clocksource calibration: 2809.789 MHz.
[    1.373242] Switching to clocksource tsc
[    1.501804] hub 2-1:1.0: USB hub found
[    1.502011] hub 2-1:1.0: 8 ports detected
[    1.573179] usb 1-1.1: new high speed USB device using ehci_hcd and address 3
[    1.581031] ata2.00: SATA link down (SStatus 0 SControl 300)
[    1.581045] ata2.01: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.591737] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.591748] ata1.01: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.597099] ata2.01: ATAPI: TSSTcorpDVD-ROM SH-D163C, SB01, max UDMA/100
[    1.613120] ata2.01: configured for UDMA/100
[    1.621332] ata1.00: ATA-8: SAMSUNG HD103SJ, 1AJ10001, max UDMA/133
[    1.621338] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.621348] ata1.01: ATAPI: HL-DT-ST BD-RE  BH10LS30, 1.00, max UDMA/133
[    1.629266] ata1.00: configured for UDMA/133
[    1.645237] ata1.01: configured for UDMA/133
[    1.651336] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HD103SJ  1AJ1 PQ: 0 ANSI: 5
[    1.651508] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.651546] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.666224] scsi 0:0:1:0: CD-ROM            HL-DT-ST BD-RE  BH10LS30  1.00 PQ: 0 ANSI: 5
[    1.678704] sd 0:0:0:0: [sda] Write Protect is off
[    1.678710] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.686895] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.686901] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.686949] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.687049] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    1.687091] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    1.688044] scsi 1:0:1:0: CD-ROM            TSSTcorp DVD-ROM SH-D163C SB01 PQ: 0 ANSI: 5
[    1.690559] sr1: scsi3-mmc drive: 1x/32x cd/rw xa/form2 cdda tray
[    1.690699] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    1.690741] sr 1:0:1:0: Attached scsi generic sg2 type 5
[    1.738977]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    1.739747] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.739952] Freeing unused kernel memory: 720k freed
[    1.740169] Write protecting the kernel text: 5352k
[    1.740228] Write protecting the kernel read-only data: 2188k
[    1.740230] NX-protecting the kernel data: 4888k
[    1.759513] <30>udev[72]: starting version 167
[    1.772868] usb 2-1.1: new low speed USB device using ehci_hcd and address 3
[    1.819276] pata_via 0000:02:00.0: version 0.3.4
[    1.819294] pata_via 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.819332] pata_via 0000:02:00.0: setting latency timer to 64
[    1.827250] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.827271] r8169 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.827306] r8169 0000:01:00.0: setting latency timer to 64
[    1.827310] r8169 0000:01:00.0: (unregistered net_device): unknown MAC, using family default
[    1.827358] r8169 0000:01:00.0: irq 40 for MSI/MSI-X
[    1.827715] r8169 0000:01:00.0: eth0: RTL8168b/8111b at 0xf8440000, 20:cf:30:6f:be:1d, XID 0c200000 IRQ 40
[    1.840489] scsi4 : pata_via
[    1.840574] scsi5 : pata_via
[    1.840717] ata5: PATA max UDMA/133 cmd 0xec00 ctl 0xe880 bmdma 0xe400 irq 17
[    1.840720] ata6: PATA max UDMA/133 cmd 0xe800 ctl 0xe480 bmdma 0xe408 irq 17
[    1.940715] usb 2-1.3: new high speed USB device using ehci_hcd and address 4
[    2.037692] usbcore: registered new interface driver uas
[    2.104511] usb 2-1.4: new full speed USB device using ehci_hcd and address 5
[    2.172258] Initializing USB Mass Storage driver...
[    2.172344] scsi6 : usb-storage 2-1.3:1.0
[    2.172424] usbcore: registered new interface driver usb-storage
[    2.172425] USB Mass Storage support registered.
[    2.188347] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input2
[    2.188426] generic-usb 0003:413C:2003.0001: input,hidraw0: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1d.0-1.1/input0
[    2.188437] usbcore: registered new interface driver usbhid
[    2.188438] usbhid: USB HID core driver
[    2.212325] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/input/input3
[    2.212400] generic-usb 0003:046D:C52B.0002: input,hidraw1: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.0-1.4/input0
[    2.214407] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.1/input/input4
[    2.214542] generic-usb 0003:046D:C52B.0003: input,hiddev0,hidraw2: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1.4/input1
[    2.216973] generic-usb 0003:046D:C52B.0004: hiddev0,hidraw3: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-1.4/input2
[    3.172262] scsi 6:0:0:0: Direct-Access     Seagate  FA GoFlex Desk   0155 PQ: 0 ANSI: 4
[    3.173470] sd 6:0:0:0: Attached scsi generic sg3 type 0
[    3.174060] sd 6:0:0:0: [sdb] 3907029167 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    3.174609] sd 6:0:0:0: [sdb] Write Protect is off
[    3.174614] sd 6:0:0:0: [sdb] Mode Sense: 1c 00 00 00
[    3.175550] sd 6:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.178313]  sdb: sdb1
[    3.180545] sd 6:0:0:0: [sdb] Attached SCSI disk
[   12.781103] Adding 14195708k swap on /dev/sda5.  Priority:-1 extents:1 across:14195708k
[   12.812775] <30>udev[323]: starting version 167
[   12.839463] lp: driver loaded but no devices found
[   12.913240] parport_pc 00:0b: reported by Plug and Play ACPI
[   12.913285] parport0: PC-style at 0x378, irq 7 [PCSPP]
[   12.981630] ip_tables: (C) 2000-2006 Netfilter Core Team
[   13.024646] type=1400 audit(1309255209.703:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=601 comm="apparmor_parser"
[   13.024725] type=1400 audit(1309255209.703:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=611 comm="apparmor_parser"
[   13.025158] type=1400 audit(1309255209.703:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=601 comm="apparmor_parser"
[   13.025239] type=1400 audit(1309255209.703:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=611 comm="apparmor_parser"
[   13.025484] type=1400 audit(1309255209.703:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=601 comm="apparmor_parser"
[   13.025567] type=1400 audit(1309255209.703:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=611 comm="apparmor_parser"
[   13.075533] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   13.111037] lp0: using parport0 (interrupt-driven).
[   13.114245] [drm] Initialized drm 1.1.0 20060810
[   13.131053] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   13.171942] r8169 0000:01:00.0: eth0: link down
[   13.172106] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.270931] cfg80211: Calling CRDA to update world regulatory domain
[   13.278994] ppdev: user-space parallel port driver
[   13.307146] cfg80211: World regulatory domain updated:
[   13.307149] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.307151] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.307153] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.307155] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.307157] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.307158] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.338998] type=1400 audit(1309255210.019:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=891 comm="apparmor_parser"
[   13.339535] type=1400 audit(1309255210.019:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=891 comm="apparmor_parser"
[   13.339919] type=1400 audit(1309255210.019:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=891 comm="apparmor_parser"
[   13.341485] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.341490] i915 0000:00:02.0: setting latency timer to 64
[   13.346122] type=1400 audit(1309255210.023:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=895 comm="apparmor_parser"
[   13.354226] mtrr: type mismatch for e0000000,10000000 old: write-back new: write-combining
[   13.354228] [drm] MTRR allocation failed.  Graphics performance may suffer.
[   13.354842] i915 0000:00:02.0: irq 41 for MSI/MSI-X
[   13.354846] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   13.354847] [drm] Driver supports precise vblank timestamp query.
[   13.424455] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   13.428832] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   13.428835] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   13.428837] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   13.428839] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   13.428841] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   13.428843] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   13.428845] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   13.428846] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   13.428848] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   13.428850] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   13.428851] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   13.428853] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   13.428855] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   13.428857] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   13.428858] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   13.428860] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   13.428862] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   13.428864] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   13.428865] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   13.428867] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   13.428869] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   13.428871] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   13.428872] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   13.428874] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   13.428876] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   13.428878] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   13.428879] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   13.428881] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[   13.445143] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   13.445672] Registered led device: rt2800usb-phy0::radio
[   13.445689] Registered led device: rt2800usb-phy0::assoc
[   13.445709] Registered led device: rt2800usb-phy0::quality
[   13.447373] usbcore: registered new interface driver rt2800usb
[   13.447903] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   13.452037] rtusb init --->
[   13.452479] usbcore: registered new interface driver rt2870
[   13.611330] Console: switching to colour frame buffer device 240x67
[   13.611375] fb0: inteldrmfb frame buffer device
[   13.611377] drm: registered panic notifier
[   13.618417] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   13.618467] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.618538] HDA Intel 0000:00:1b.0: irq 42 for MSI/MSI-X
[   13.618622] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.705886] hda_codec: ALC887: BIOS auto-probing.
[   13.720068] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   17.076834] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.002169] wlan0: authenticate with 00:26:5a:cf:e4:16 (try 1)
[   26.003699] wlan0: authenticated
[   27.614259] wlan0: associate with 00:26:5a:cf:e4:16 (try 1)
[   27.617135] wlan0: RX AssocResp from 00:26:5a:cf:e4:16 (capab=0x431 status=0 aid=2)
[   27.617141] wlan0: associated
[   27.644568] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   27.653874] Intel AES-NI instructions are not detected.
[   27.670350] padlock_aes: VIA PadLock not detected.
[   37.697305] wlan0: no IPv6 routers present
[   73.280292] wlan0: deauthenticating from 00:26:5a:cf:e4:16 by local choice (reason=3)
[   74.911138] cfg80211: All devices are disconnected, going to restore regulatory settings
[   74.911146] cfg80211: Restoring regulatory settings
[   74.911153] cfg80211: Calling CRDA to update world regulatory domain
[   74.917378] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   74.917385] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   74.917389] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   74.917394] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   74.917397] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   74.917402] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   74.917406] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   74.917410] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   74.917414] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   74.917418] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   74.917422] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   74.917426] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   74.917430] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   74.917434] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   74.917438] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   74.917443] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   74.917446] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   74.917451] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   74.917454] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   74.917459] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   74.917462] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   74.917467] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   74.917471] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   74.917475] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   74.917479] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   74.917483] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   74.917487] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   74.917491] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[   74.917496] cfg80211: World regulatory domain updated:
[   74.917499] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   74.917503] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   74.917508] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   74.917512] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   74.917516] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   74.917520] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)





6) Network Configuration




$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 06
       serial: 20:cf:30:6f:be:1d
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:40 ioport:d800(size=256) memory:f6fff000-f6ffffff memory:f6ff8000-f6ffbfff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:1.1
       logical name: wlan0
       serial: 00:1f:1f:e3:50:1c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=2.6.38-8-generic-pae firmware=0.12 link=no multicast=yes wireless=IEEE 802.11bgn





7) Scan for networks





$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results



8) Ubuntu Version



$ uname -mr
2.6.38-8-generic-pae i686


9)Kernal/Architechture


$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                                                       [ OK ]

---

