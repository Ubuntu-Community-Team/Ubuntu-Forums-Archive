---
title: "Belkin f5d8055 v2 won't connect to hidden network via mac ad filtering / Ubuntu 11.04"
date: 2011-09-27
forum: Networking &amp; Wireless
---

### Post by glefix on 2011-09-27
[B]2. Update:
Must have mistaken something, maybe it was another network.
Belkin still doesn't connect! I appreciate any solution ;)[/B]

[B]1. Update:
I just tried to connect with BSSID information (there are 
two routers with different BSSID under the same SSID).
Works like a charme, so problem solved for me.
Anyhow, it still doesn't work without BSSID.[/B]

Hello all!
As mentioned in the title, the Belkin f5d8055 v2 won't connect to a hidden network with mac address filtering on Ubuntu 11.04.
It does connect to an open network (without any security settings).
It also worked on Ubuntu 10.04 LTS with a driver I installed by following this [http://ubuntuforums.org/showthread.php?t=1353044](http://ubuntuforums.org/showthread.php?t=1353044) and that [http://ubuntuforums.org/showthread.php?t=1387483](http://ubuntuforums.org/showthread.php?t=1387483) How-to.
Also the built in Atheros AR9285 connects to the hidden network when given the same mac address which the Belkin has.

Thanks for any help.

Felix

Here is some info:

1 ) Machine Brand and Model
```
Asrock Ion 330
```2 ) Wireless Brand, Model and Wireless Chipset:
```
lspci -nn | grep -i net
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP79 Ethernet [10de:0ab0] (rev b1)
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
-e
---------------
lsusb
Bus 001 Device 004: ID 050d:825b Belkin Components F5D8055 N+ Wireless Adapter v2000 [Ralink RT3070]
-e 
```3 ) check interface:
```
iwconfig
wlan0 Ralink STA ESSID:"" Nickname:"RT2870STA"
Mode:Auto Frequency=2.462 GHz Access Point: Not-Associated
Bit Rate:1 Mb/s
RTS thr:off Fragment thr:off
Link Quality=70/100 Signal level:-67 dBm Noise level:-95 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

wlan1 IEEE 802.11bgn ESSID:off/any
Mode:Managed Access Point: Not-Associated Tx-Power=17 dBm
Retry long limit:7 RTS thr:off Fragment thr:off
Power Management:off

-e
---------------
ifconfig
eth0 Link encap:Ethernet HWaddr 90:e6:ba:f2:77:69
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:21 Base address:0xa000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:448 errors:0 dropped:0 overruns:0 frame:0
TX packets:448 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:34944 (34.9 KB) TX bytes:34944 (34.9 KB)

wlan0 Link encap:Ethernet HWaddr 00:22:75:40:c7:f7
inet6 addr: fe80::222:75ff:fe40:c7f7/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:19740 errors:3 dropped:0 overruns:0 frame:0
TX packets:149 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:2848440 (2.8 MB) TX bytes:10548 (10.5 KB)

wlan1 Link encap:Ethernet HWaddr 00:25:d3:88:cd:88
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

```4 ) Check for modules:
```
Module Size Used by
parport_pc 32111 0
ppdev 12849 0
lp 13349 0
dm_crypt 22463 0
parport 36746 3 parport_pc,ppdev,lp
snd_hda_codec_realtek 255820 1
binfmt_misc 13213 1
snd_hda_intel 24140 2
snd_hda_codec 90901 2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep 13274 1 snd_hda_codec
snd_pcm 80244 2 snd_hda_intel,snd_hda_codec
snd_seq_midi 13132 0
ir_lirc_codec 12770 0
snd_rawmidi 25269 1 snd_seq_midi
lirc_dev 18720 1 ir_lirc_codec
ir_sony_decoder 12493 0
ir_jvc_decoder 12490 0
rc_rc6_mce 12454 0
ir_rc6_decoder 12490 0
ir_rc5_decoder 12490 0
ir_nec_decoder 12490 0
nuvoton_cir 17643 0
rc_core 25760 9 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,rc_rc6_mce,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,nuvoton_cir
snd_seq_midi_event 14475 1 snd_seq_midi
joydev 17322 0
snd_seq 51291 2 snd_seq_midi,snd_seq_midi_event
arc4 12473 2
rt2870sta 410104 1
ath9k 103633 0
crc_ccitt 12595 1 rt2870sta
snd_timer 28659 2 snd_pcm,snd_seq
mac80211 257001 1 ath9k
snd_seq_device 14110 3 snd_seq_midi,snd_rawmidi,snd_seq
ath9k_common 13611 1 ath9k
snd 55295 13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath9k_hw 300328 2 ath9k,ath9k_common
soundcore 12600 1 snd
psmouse 73312 0
ath 19141 2 ath9k,ath9k_hw
i2c_nforce2 12906 0
cfg80211 156212 3 ath9k,mac80211,ath
shpchp 32345 0
serio_raw 12990 0
snd_page_alloc 14073 2 snd_hda_intel,snd_pcm
squashfs 35973 1
aufs 159344 4376
nls_iso8859_1 12617 1
nls_cp437 12751 1
vfat 17335 1
fat 55505 1 vfat
dm_raid45 88410 0
xor 21860 1 dm_raid45
btrfs 527341 0
zlib_deflate 26594 1 btrfs
libcrc32c 12543 1 btrfs
hid_logitech 17421 0
ff_memless 12945 1 hid_logitech
usbhid 41704 1 hid_logitech
hid 77084 2 hid_logitech,usbhid
nouveau 621970 2
ttm 65184 1 nouveau
usb_storage 43946 1
drm_kms_helper 40745 1 nouveau
uas 17676 0
drm 180037 4 nouveau,ttm,drm_kms_helper
i2c_algo_bit 13184 1 nouveau
ahci 21591 0
video 18951 1 nouveau
libahci 25548 1 ahci
forcedeth 58190 0

```5 ) Kernel boot messages
```
Will follow
```6 ) Network configuration
```
*-network               
       description: Ethernet interface
       product: MCP79 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: b1
       serial: 90:e6:ba:f2:77:69
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: irq:21 memory:fae7d000-fae7dfff ioport:d080(size=8) memory:fae7e800-fae7e8ff memory:fae7e400-fae7e40f
  *-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:25:d3:88:cd:88
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-8-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 memory:febf0000-febfffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: firewire@1
       logical name: wlan1
       serial: 00:22:75:40:c7:f7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=usb multicast=yes wireless=Ralink STA

```7 ) Scan for networks:
```
wlan0 Scan completed :
Cell 01 - Address: 00:0F:A3:10:07:38
Protocol:802.11b/g
ESSID:""
Mode:Managed
Channel:1
Quality:47/100 Signal level:-71 dBm Noise level:-95 dBm
Encryption key:off
Bit Rates:11 Mb/s
Cell 02 - Address: 7C:4F:B5:48:1E:9F
Protocol:802.11b/g/n
ESSID:"EasyBox-481E09"
Mode:Managed
Channel:1
Quality:47/100 Signal level:-71 dBm Noise level:-95 dBm
Encryption key:on
Bit Rates:144 Mb/s
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
Preauthentication Supported
Cell 03 - Address: 88:25:2C:B4:8F:48
Protocol:802.11b/g/n
ESSID:"halmb0"
Mode:Managed
Channel:2
Quality:18/100 Signal level:-83 dBm Noise level:-95 dBm
Encryption key:on
Bit Rates:150 Mb/s
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
Cell 04 - Address: 7C:4F:B5:09:25:A6
Protocol:802.11b/g/n
ESSID:"ALICE-WLAN47"
Mode:Managed
Channel:2
Quality:42/100 Signal level:-73 dBm Noise level:-95 dBm
Encryption key:on
Bit Rates:150 Mb/s
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
Preauthentication Supported
Cell 05 - Address: 7C:4F:B5:1F:4D:DD
Protocol:802.11b/g/n
ESSID:"ALICE-WLAN92"
Mode:Managed
Channel:2
Quality:2/100 Signal level:-89 dBm Noise level:-95 dBm
Encryption key:on
Bit Rates:150 Mb/s
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
Preauthentication Supported
Cell 06 - Address: 7C:4F:B5:7C:CD:78
Protocol:802.11b/g/n
ESSID:"ALICE-WLAN49"
Mode:Managed
Channel:2
Quality:18/100 Signal level:-83 dBm Noise level:-95 dBm
Encryption key:on
Bit Rates:150 Mb/s
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
Cell 07 - Address: 00:1D:19:6A:FD:6E
Protocol:802.11b/g
ESSID:"WLAN-6AFD40"
Mode:Managed
Channel:3
Quality:63/100 Signal level:-65 dBm Noise level:-95 dBm
Encryption key:on
Bit Rates:18 Mb/s
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
Cell 08 - Address: 00:1A:2A:51:5D:2B
Protocol:802.11b/g
ESSID:"Brando"
Mode:Managed
Channel:4
Quality:2/100 Signal level:-89 dBm Noise level:-95 dBm
Encryption key:on
Bit Rates:18 Mb/s
Cell 09 - Address: 00:3A:98:29:A9:B1
Protocol:802.11b/g
ESSID:""
Mode:Managed
Channel:6
Quality:7/100 Signal level:-87 dBm Noise level:-95 dBm
Encryption key:on
Bit Rates:18 Mb/s
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (1) : TKIP
Authentication Suites (1) : PSK
Cell 10 - Address: 00:24:FE:70:19:D7
Protocol:802.11b/g
ESSID:"FRITZ!Box Fon WLAN 7113"
Mode:Managed
Channel:6
Quality:37/100 Signal level:-75 dBm Noise level:-95 dBm
Encryption key:on
Bit Rates:11 Mb/s
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (1) : TKIP
Authentication Suites (1) : PSK
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
Cell 11 - Address: 34:08:04:B8:AD:94
Protocol:802.11b/g/n
ESSID:"dlink"
Mode:Managed
Channel:6
Quality:7/100 Signal level:-87 dBm Noise level:-95 dBm
Encryption key:on
Bit Rates:300 Mb/s
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
Cell 12 - Address: 00:3A:98:29:A9:B3
Protocol:802.11b/g
ESSID:"moevlm05"
Mode:Managed
Channel:6
Quality:7/100 Signal level:-87 dBm Noise level:-95 dBm
Encryption key:on
Bit Rates:18 Mb/s
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (2) : 802.1x Proprietary
Cell 13 - Address: 00:0F:A3:10:07:42
Protocol:802.11b/g
ESSID:""
Mode:Managed
Channel:7
Quality:7/100 Signal level:-87 dBm Noise level:-95 dBm
Encryption key:off
Bit Rates:11 Mb/s
Cell 14 - Address: 88:25:2C:C9:21:CC
Protocol:802.11b/g/n
ESSID:"ALICE-WLAN20"
Mode:Managed
Channel:8
Quality:42/100 Signal level:-73 dBm Noise level:-95 dBm
Encryption key:on
Bit Rates:150 Mb/s
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
Cell 15 - Address: 00:24:FE:A4:43:C1
Protocol:802.11b/g/n
ESSID:"o2 Sarhan"
Mode:Managed
Channel:8
Quality:7/100 Signal level:-87 dBm Noise level:-95 dBm
Encryption key:on
Bit Rates:18 Mb/s
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (1) : TKIP
Authentication Suites (1) : PSK
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
Cell 16 - Address: 96:34:2F:FD:7B:69
Protocol:802.11b
ESSID:"A9F1BDF1DAB1NVT4F4F59"
Mode:Ad-Hoc
Channel:10
Quality:13/100 Signal level:-85 dBm Noise level:-95 dBm
Encryption key:on
Bit Rates:11 Mb/s
Cell 17 - Address: 00:0F:A3:10:07:49
Protocol:802.11b/g
ESSID:""
Mode:Managed
Channel:11
Quality:18/100 Signal level:-83 dBm Noise level:-95 dBm
Encryption key:off
Bit Rates:11 Mb/s
Cell 18 - Address: 00:16:E3:72:74:EF
Protocol:802.11b/g
ESSID:"ALICE-WLAN"
Mode:Managed
Channel:11
Quality:18/100 Signal level:-83 dBm Noise level:-95 dBm
Encryption key:on
Bit Rates:54 Mb/s
Cell 19 - Address: 00:1B:D4:86:AB:00
Protocol:802.11b/g
ESSID:"Telekom"
Mode:Managed
Channel:11
Quality:63/100 Signal level:-65 dBm Noise level:-95 dBm
Encryption key:off
Bit Rates:18 Mb/s
Cell 20 - Address: 00:1A:4F:91:BC:89
Protocol:802.11b/g
ESSID:"WLAN-001A4F91BC89"
Mode:Managed
Channel:11
Quality:0/100 Signal level:-91 dBm Noise level:-95 dBm
Encryption key:on
Bit Rates:11 Mb/s
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (1) : TKIP
Authentication Suites (1) : PSK
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK

wlan1 Scan completed :
Cell 01 - Address: 88:25:2C:C9:21:CC
Channel:8
Frequency:2.447 GHz (Channel 8)
Quality=28/70 Signal level=-82 dBm
Encryption key:on
ESSID:"ALICE-WLAN20"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
18 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
Mode:Master
Extra:tsf=00000049b34cb7d6
Extra: Last beacon: 592ms ago
IE: Unknown: 000C414C4943452D574C414E3230
IE: Unknown: 010882848B961224486C
IE: Unknown: 030108
IE: Unknown: 2A0100
IE: Unknown: 32040C183060
IE: Unknown: 2D1A6E1017FF00000001000000000000000000000000000000000000
IE: Unknown: 3D1608070000000000000000000000000000000000000000
IE: Unknown: 3E0100
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
IE: Unknown: 7F0101
IE: Unknown: DD900050F204104A00011010440001021041000100103B000103104700100000000000000003000088252CC921CC1021000848616E73654E657410230008415237353035535710240007312E30302E31361042000A303131313035353232301054000800060050F20400011011001D48616E73654E657420576972656C65737320526F757465722857464129100800020084
IE: Unknown: DD07000C4300000000
IE: Unknown: 0706444520010D10
IE: Unknown: DD1E00904C336E1017FF00000001000000000000000000000000000000000000
IE: Unknown: DD1A00904C3408070000000000000000000000000000000000000000
Cell 02 - Address: 00:1B:D4:86:AB:00
Channel:11
Frequency:2.462 GHz (Channel 11)
Quality=30/70 Signal level=-80 dBm
Encryption key:off
ESSID:"Telekom"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
11 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=00000626f1749208
Extra: Last beacon: 324ms ago
IE: Unknown: 000754656C656B6F6D
IE: Unknown: 010882848B0C12961824
IE: Unknown: 03010B
IE: Unknown: 2A0106
IE: Unknown: 32043048606C
IE: Unknown: DD06004096010100
IE: Unknown: DD050040960304
IE: Unknown: DD1600409604000207A4000023A400004243000062320000
IE: Unknown: DD050040960B01
IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
Cell 03 - Address: 7C:4F:B5:48:1E:9F
Channel:1
Frequency:2.412 GHz (Channel 1)
Quality=17/70 Signal level=-93 dBm
Encryption key:on
ESSID:"EasyBox-481E09"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
18 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
Mode:Master
Extra:tsf=0000002b272c916c
Extra: Last beacon: 1048ms ago
IE: Unknown: 000E45617379426F782D343831453039
IE: Unknown: 010882848B961224486C
IE: Unknown: 030101
IE: Unknown: 2A0104
IE: Unknown: 32040C183060
IE: Unknown: 2D1A6C0017FFFF000000000000000000000000000000000000000000
IE: Unknown: 3D1601000500000000000000000000000000000000000000
IE: Unknown: 3E0100
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
Preauthentication Supported
IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
IE: Unknown: 0B050001847A12
IE: Unknown: 7F0101
IE: Unknown: DD8E0050F204104A00011010440001021041000100103B00010310470010000000000000000300007C4FB5481E9F1021000B436F72706F726174696F6E102300094152563735324450571024000933302E30352E3230371042000B52313039303037383339321054000800060050F204000110110014576972656C65737320526F757465722857464129100800020004
IE: Unknown: 0706444520010D10
IE: Unknown: DD1E00904C336C0017FFFF000000000000000000000000000000000000000000
IE: Unknown: DD1A00904C3401000500000000000000000000000000000000000000
Cell 04 - Address: 00:1D:19:6A:FD:6E
Channel:3
Frequency:2.422 GHz (Channel 3)
Quality=27/70 Signal level=-83 dBm
Encryption key:on
ESSID:"WLAN-6AFD40"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
11 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=0000004108583d60
Extra: Last beacon: 812ms ago
IE: Unknown: 000B574C414E2D364146443430
IE: Unknown: 010882848B0C12961824
IE: Unknown: 030103
IE: Unknown: DD8C0050F204104A00011010440001021041000100103B0001031047001000000000000000011000001D196AFD6C1021000B436F72706F726174696F6E1023000956475634353038425710240008312E31392E3030301042000A4A3830333034383339301054000800060050F204000110110014576972656C65737320526F757465722857464129100800020004
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
IE: Unknown: 2A0100
IE: Unknown: 32043048606C
IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
Cell 05 - Address: 7C:4F:B5:09:25:A6
Channel:2
Frequency:2.417 GHz (Channel 2)
Quality=19/70 Signal level=-91 dBm
Encryption key:on
ESSID:"ALICE-WLAN47"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
18 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
Mode:Master
Extra:tsf=000000070110f54a
Extra: Last beacon: 856ms ago
IE: Unknown: 000C414C4943452D574C414E3437
IE: Unknown: 010882848B961224486C
IE: Unknown: 030102
IE: Unknown: 2A0100
IE: Unknown: 32040C183060
IE: Unknown: 2D1A6E1017FF00000001000000000000000000000000000000000000
IE: Unknown: 3D1602050000000000000000000000000000000000000000
IE: Unknown: 3E0100
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
Preauthentication Supported
IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
IE: Unknown: 7F0101
IE: Unknown: DD900050F204104A00011010440001021041000100103B00010310470010000000000000000300007C4FB50925A61021000848616E73654E657410230008415237353035535710240007312E30302E31311042000A313031313031313334371054000800060050F20400011011001D48616E73654E657420576972656C65737320526F757465722857464129100800020084
IE: Unknown: DD07000C4300000000
IE: Unknown: 0706444520010D10
IE: Unknown: DD1E00904C336E1017FF00000001000000000000000000000000000000000000
IE: Unknown: DD1A00904C3402050000000000000000000000000000000000000000
Cell 06 - Address: 00:1A:4F:20:A1:13
Channel:11
Frequency:2.462 GHz (Channel 11)
Quality=23/70 Signal level=-87 dBm
Encryption key:on
ESSID:"WLAN-001A4F20A113"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=0000001b1b1fa4e0
Extra: Last beacon: 416ms ago
IE: Unknown: 0011574C414E2D303031413446323041313133
IE: Unknown: 010482848B96
IE: Unknown: 03010B
IE: Unknown: 2A0107
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
IE: Unknown: 32080C1218243048606C
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (1) : TKIP
Authentication Suites (1) : PSK
IE: Unknown: DD0A0800280101000200FF0F
IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

```8 ) Ubuntu Version:
```
ubuntu@ubuntu:/$ lsb_release -d
Description:    Ubuntu 11.04
```[B]9 ) Kernel/architecture (including 32 vs. 64 bit): 
[/B]```
ubuntu@ubuntu:/$ uname -mr
2.6.38-8-generic i686
```[B]10 ) Restarting the network:
[/B]```
ubuntu@ubuntu:/$  sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...    
```

---

### Post by praseodym on 2011-09-27
Do you need both device in parallel? Maybe this just doesnt work. You can try this udev-rule

[http://ubuntuforums.org/showpost.php?p=11247931&postcount=13](http://ubuntuforums.org/showpost.php?p=11247931&postcount=13)

replace [COLOR="Red"]b43[/COLOR] in that file with [COLOR="Red"]ath9k[/COLOR]. Did you install linux-firmware for the rt2870sta? Maybe you try the oneiric package.

---

### Post by glefix on 2011-09-28
> **praseodym said:**
> Do you need both device in parallel? Maybe this just doesnt work. You can try this udev-rule

[http://ubuntuforums.org/showpost.php?p=11247931&postcount=13](http://ubuntuforums.org/showpost.php?p=11247931&postcount=13)

replace [COLOR=Red]b43[/COLOR] in that file with [COLOR=Red]ath9k[/COLOR]. Did you install linux-firmware for the rt2870sta? Maybe you try the oneiric package.


I've already disabled the onboard wlan chip (the Atheros) in the bios, but that didn't work too. I'll give your script a try later anyway.
thanks

---

