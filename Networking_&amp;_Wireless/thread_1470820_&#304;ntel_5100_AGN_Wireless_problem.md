---
title: "&#304;ntel 5100 AGN Wireless problem"
date: 2010-05-03
forum: Networking &amp; Wireless
---

### Post by Ugurcan377 on 2010-05-03
installed 10.04 and first 30min-1hr there was perfect internet connections and after that time a server connections error occured neither changing dns nor reinstalling ubuntu solved problem i am sending outputs of some codes i hope this will be sufficent to solve the problem(i am writing from double boot windows 7)
```
1 ) Machine Brand and Model (PC/Laptop):
hp pavilion dv6 1144et
2-Wireless Brand, Model and Wireless Chipset:
02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
3-check interface:
wlan0     IEEE 802.11abgn  ESSID:"Ergun"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1E:40:CE:5B:5D   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
4-Check for modules:
Module                  Size  Used by
nls_iso8859_1           4633  1 
nls_cp437               6351  1 
vfat                   10802  1 
fat                    55350  1 vfat
snd_hda_codec_atihdmi     3023  1 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0 
vgastate                9857  1 vga16fb
binfmt_misc             7960  1 
ppdev                   6375  0 
rfcomm                 40329  4 
sco                     9617  2 
bridge                 53152  0 
stp                     2171  1 bridge
bnep                   11820  2 
l2cap                  34774  16 rfcomm,bnep
snd_hda_codec_idt      61418  1 
arc4                    1473  2 
snd_hda_intel          25645  2 
snd_hda_codec          85727  3 snd_hda_codec_atihdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87850  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
joydev                 11072  0 
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23388  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iwlagn                121577  0 
radeon                739595  3 
snd_timer              23553  2 snd_pcm,snd_seq
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iwlcore               124955  1 iwlagn
jmb38x_ms               8643  0 
mac80211              238128  2 iwlagn,iwlcore
ttm                    60815  1 radeon
drm_kms_helper         30742  1 radeon
uvcvideo               62403  0 
videodev               40486  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    12020  1 videodev
btusb                  12969  2 
bluetooth              58621  9 rfcomm,sco,bnep,l2cap,btusb
snd                    70978  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                64608  0 
serio_raw               4918  0 
memstick               10121  1 jmb38x_ms
sdhci_pci               6700  0 
sdhci                  17928  1 sdhci_pci
cfg80211              148386  3 iwlagn,iwlcore,mac80211
lirc_ene0100            7532  0 
lirc_dev               11302  1 lirc_ene0100
drm                   198770  5 radeon,ttm,drm_kms_helper
i2c_algo_bit            6024  1 radeon
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
hp_accel               12168  0 
lis3lv02d               7583  1 hp_accel
input_polldev           3106  1 lis3lv02d
video                  20623  0 
led_class               3732  3 iwlcore,sdhci,hp_accel
output                  2503  1 video
lp                      9336  0 
intel_agp              29225  0 
parport                37160  2 ppdev,lp
usbhid                 40988  0 
hid                    83376  1 usbhid
usb_storage            49833  1 
ohci1394               30260  0 
ieee1394               94675  1 ohci1394
ahci                   37646  2 
r8169                  39554  0 
mii                     5237  1 r8169
sorry i coudn't found which one is wireless module
5-Kernel boot messages
[   45.453098] wlan0: deauthenticating from 00:1e:40:ce:5b:5d by local choice (reason=3)
[   45.453135] wlan0: direct probe to AP 00:1e:40:ce:5b:5d (try 1)
[   45.456552] wlan0: direct probe responded
[   45.456556] wlan0: authenticate with AP 00:1e:40:ce:5b:5d (try 1)
[   45.458553] wlan0: authenticated
[   45.458576] wlan0: associate with AP 00:1e:40:ce:5b:5d (try 1)
[   45.461008] wlan0: RX AssocResp from 00:1e:40:ce:5b:5d (capab=0x411 status=0 aid=1)
[   45.461012] wlan0: associated
[   45.472190] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   56.370032] wlan0: no IPv6 routers present
6-Network configuration
  *-network               
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:22:fa:b8:01:b8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.3 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:33 memory:d9000000-d9001fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:23:8b:b6:fa:f5
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:30 ioport:5000(size=256) memory:d1010000-d1010fff(prefetchable) memory:d1000000-d100ffff(prefetchable) memory:d1020000-d102ffff(prefetchable)
7-Scan for networks
wlan0     Scan completed :
          Cell 01 - Address: 00:1E:40:CE:5B:5D
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"Ergun"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000008dc94a8a0
                    Extra: Last beacon: 2190ms ago
                    IE: Unknown: 0005457267756E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180201F4
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
8-Ubuntu Version
Description:	Ubuntu 10.04 LTS
9-Kernel/architecture
2.6.32-21-generic x86_64
10) Restarting the network
 * Reconfiguring network interfaces...                                                    Ignoring unknown interface wlan0=wlan0.
                                                                                   [ OK ]

```

---

### Post by allblack21 on 2010-05-03
I have the same intel 5100 card and can also not access the Internet through my wireless lan. It will connect just fine but I can not ping the router or other computers or connect to the Internet. Perhaps this is an issue with this particular card. I can however connect if I use the ethernet port directly to the router.

---

### Post by allblack21 on 2010-05-03
Here's the Network information

1) Lenovo SL510 laptop
2)05:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
3)ifconfig

wlan0     Link encap:Ethernet  HWaddr 00:24:d6:38:89:a8  
          inet addr:192.168.1.52  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:d6ff:fe38:89a8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2609 errors:0 dropped:0 overruns:0 frame:0
          TX packets:344 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1044765 (1.0 MB)  TX bytes:35987 (35.9 KB)

iwconfig

wlan0     IEEE 802.11abgn  ESSID:"flipper"  
          Mode:Managed  Frequency:2.462 GHz  Access Point:    00:22:CF:21:3F:28   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

4)iwlagn                105566  0 
  snd_timer              19098  2 snd_pcm,snd_seq
  snd_seq_device          5700  5     snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
  iwlcore               105922  1 iwlagn
  mac80211              204922  2 iwlagn,iwlcore

5)
701 name="/usr/lib/connman/scripts/dhclient-script"
[   13.589679] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   13.589682] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   13.589743] iwlagn 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   13.589752] iwlagn 0000:05:00.0: setting latency timer to 64
[   13.589788] iwlagn 0000:05:00.0: Detected Intel Wireless WiFi Link 5100AGN RE

[   13.710634] iwlagn 0000:05:00.0: Tunable channels: 13 802.11bg, 24 802.11a ch
[   13.710721] iwlagn 0000:05:00.0: irq 33 for MSI/MSI-X

[   14.809992] iwlagn 0000:05:00.0: firmware: requesting iwlwifi-5000-2.ucode

[   14.844059] iwlagn 0000:05:00.0: loaded firmware version 8.24.2.12

[   31.219149] padlock: VIA PadLock not detected.
[   37.211043] wlan0: deauthenticating from 00:22:cf:21:3f:28 by local choice (reason=3)
[   37.211198] wlan0: direct probe to AP 00:22:cf:21:3f:28 (try 1)
[   37.213545] wlan0: direct probe responded
[   37.213549] wlan0: authenticate with AP 00:22:cf:21:3f:28 (try 1)
[   37.214950] wlan0: authenticated
[   37.214967] wlan0: associate with AP 00:22:cf:21:3f:28 (try 1)
[   37.225514] wlan0: RX AssocResp from 00:22:cf:21:3f:28 (capab=0xc11 status=0 aid=1)
[   37.225518] wlan0: associated
[   37.226913] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   48.080022] wlan0: no IPv6 routers present
[  157.775047] r8169: eth0: link up
[  157.775239] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  168.600051] eth0: no IPv6 routers present
[  181.891946] r8169: eth0: link down
[ 1073.081178] iwlagn 0000:05:00.0: iwl_tx_agg_start on ra = 00:22:cf:21:3f:28 tid = 0

6)Network Configuraton
*-network               
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 00
       serial: 00:24:d6:38:89:a8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.52 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:33 memory:f2200000-f2201fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:26:9e:78:b0:c3
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.21 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:30 ioport:3000(size=256) memory:f2010000-f2010fff(prefetchable) memory:f2000000-f200ffff(prefetchable) memory:f2020000-f203ffff(prefetchable)

7)wlan0     Scan completed :
          Cell 01 - Address: 00:22:CF:21:3F:28
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:on
                    ESSID:"flipper"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003245109495
                    Extra: Last beacon: 22744ms ago
                    IE: Unknown: 0007666C6970706572
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160B000400000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: DD1E00904C33EE1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C340B000400000000000000000000000000000000000000

8)Description:    Ubuntu 10.04 LTS
9)2.6.32-22-generic i686
10) Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]

---

### Post by samiux on 2010-05-05
The workaround would be disabled the N mode of the Intel 5100 AGN wireless card at the moment.  My solution is as the following :

[https://bugs.launchpad.net/ubuntu/+bug/575492](https://bugs.launchpad.net/ubuntu/+bug/575492)

Samiux

---

### Post by brunjes on 2010-05-06
> **samiux said:**
> The workaround would be disabled the N mode of the Intel 5100 AGN wireless card at the moment.  My solution is as the following :

[https://bugs.launchpad.net/ubuntu/+bug/575492](https://bugs.launchpad.net/ubuntu/+bug/575492)

Samiux

I can confirm that Samiux's fix worked for my HP Pavilion dv6 (which also uses Intel 5100 AGN wireless). I'd rather not cripple my wireless to "g" speeds, but that's the only solution I've found that works so far...

Having the bug fixed is of course the desired goal!

---

### Post by jshombre on 2010-05-09
I have an Intel 5100 wireless card in my Sony VAIO laptop and have been experiencing the very same problem since upgrading to Lucid: the wireless connection is fine, but all internet connectivity is lost. Sometimes this only happens after an hour or so, at other times it only takes 5 minutes.

This was definitely not a problem with Karmic.

I've tried the workaround suggested by Samiux and it does indeed appear to cure the problem -- fingers crossed! -- but at the penalty of slowing down wireless speeds.

---

### Post by Stickarm on 2010-05-09
Same situation as everyone else. I've got a 5100 a/b/g/n (512AN_MMWG2) in a Dell Vostro A90 and after upgrading Netbook Remix 9.10 to Netbook Edition 10.04 the wireless worked fine and then disappeared after a little while. samiux's fix seems to have resolved the issue. Disabling N support works okay for me because I'm not currently accessing any N-based networks but as a general solution that workaround is a bit of a bummer.

---

