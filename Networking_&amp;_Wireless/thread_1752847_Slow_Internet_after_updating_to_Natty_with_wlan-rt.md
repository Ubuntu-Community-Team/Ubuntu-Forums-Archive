---
title: "Slow Internet after updating to Natty with wlan-rt73usb"
date: 2011-05-08
forum: Networking &amp; Wireless
---

### Post by proxximity on 2011-05-08
After updating to kubuntu 11.04 natty, I have a problem with my internet-connection. The problem happens when I use VoIP-Software like Skype or Twinkle and also when using ktorrent.

When using the mentioned software, after 30-90 seconds the internet gets very slow. In f.e. skype, I can hear the one I phoned very badly.

I use kubuntu on a desktop-PC with a Linksys USB-Wlan-Stick. Detailed information is below. Thanks for any help!

Yours,

proxxi


```
uname -a
Linux pr1-desktop 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```

```
lsusb
Bus 001 Device 004: ID 13b1:0020 Linksys WUSB54GC v1 802.11g Adapter [Ralink RT73]
```

```
egrep -v "^$|^#" /etc/network/interfaces
auto lo
iface lo inet loopback

```

```
egrep -v "^$|^#" /etc/resolv.conf
nameserver 192.168.178.1

```

```
egrep -v "^$|^#" /etc/hosts
127.0.0.1       localhost.localdomain   localhost
::1     pr1-desktop     localhost6.localdomain6 localhost6
127.0.1.1       pr1-desktop
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

```
cat /etc/udev/rules.d/70-persistent-net.rules
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x1969:0x1048 (atl1)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1f:c6:12:87:4d", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x13b1:0x0020 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1e:e5:9c:10:e3", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
```

```
ifconfig
eth0      Link encap:Ethernet  Hardware Adresse 00:1f:c6:12:87:4d  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:328 errors:0 dropped:0 overruns:0 frame:0
          TX packets:328 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:11631 (11.6 KB)  TX bytes:11631 (11.6 KB)

wlan0     Link encap:Ethernet  Hardware Adresse 00:1e:e5:9c:10:e3  
          inet Adresse:192.168.178.30  Bcast:192.168.178.255  Maske:255.255.255.0
          inet6-Adresse: fe80::21e:e5ff:fe9c:10e3/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:36789 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32642 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:31459035 (31.4 MB)  TX bytes:5974582 (5.9 MB)
```

```
route -n
Kernel-IP-Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
192.168.178.0   0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.178.1   0.0.0.0         UG    0      0        0 wlan0
```

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"wlan1337"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1F:3F:0F:B8:94   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=52/70  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:5  Invalid misc:218   Missed beacon:0
```

```
iwlist chan
lo        no frequency information.

eth0      no frequency information.

wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Current Frequency:2.437 GHz (Channel 6)
```

```
lsmod
Module                  Size  Used by
snd_hrtimer            12784  1 
binfmt_misc            17565  1 
vboxnetadp             13340  0 
vboxnetflt             28297  0 
vboxdrv               252684  2 vboxnetadp,vboxnetflt
parport_pc             36959  0 
ppdev                  17113  0 
sha256_generic         21031  4 
cryptd                 20510  0 
aes_x86_64             17208  1658 
aes_generic            38279  1 aes_x86_64
dm_crypt               22993  2 
arc4                   12529  2 
snd_hda_codec_hdmi     28103  1 
snd_hda_codec_realtek   336693  1 
snd_usb_audio         112426  3 
snd_usbmidi_lib        25139  1 snd_usb_audio
rt73usb                27406  0 
rt2x00usb              20330  1 rt73usb
rt2x00lib              49235  2 rt73usb,rt2x00usb
snd_hda_intel          33211  4 
mac80211              294370  2 rt2x00usb,rt2x00lib
snd_seq_midi           13324  0 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  2 snd_usb_audio,snd_hda_codec
snd_pcm                96625  4 snd_hda_codec_hdmi,snd_usb_audio,snd_hda_intel,snd_hda_codec
cfg80211              178528  2 rt2x00lib,mac80211
snd_rawmidi            30486  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  3 snd_seq_midi,snd_seq_midi_event
joydev                 17606  0 
snd_timer              29602  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    67382  27 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_usb_audio,snd_usbmidi_lib,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
serio_raw              13166  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
asus_atk0110           17976  0 
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
radeon                982197  3 
ttm                    76664  1 radeon
firewire_ohci          40370  0 
drm_kms_helper         42136  1 radeon
ahci                   25951  0 
drm                   227495  5 radeon,ttm,drm_kms_helper
firewire_core          62646  1 firewire_ohci
pata_jmicron           12747  0 
crc_itu_t              12707  2 rt73usb,firewire_core
libahci                26642  1 ahci
i2c_algo_bit           13400  1 radeon
atl1                   36507  0 
```

> cat /var/lib/NetworkManager/NetworkManager.state
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

```
cat /etc/NetworkManager/nm-system-settings.conf
cat: /etc/NetworkManager/nm-system-settings.conf: Datei oder Verzeichnis nicht gefunden
```

```
dmesg | egrep 'net|eth|sky|sis|via|3c3|3c5|e100|8139|8169|acx|air|ath|ar91|atme|at7|herm|iwl|ipw|rtl8|r81|rt2|rt6|rt7|tg3|ssb|wl|b43|b44|ori|pri|p5|zd|ndis|wmi|rt73usb'
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff8800cfc00000 s84416 r8192 d22080 u524288
[    0.000000] pcpu-alloc: s84416 r8192 d22080 u524288 alloc=1*2097152
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.013054] Initializing cgroup subsys net_cls
[    0.013098] CPU0: Thermal monitoring enabled (TM2)
[    0.310903] print_constraints: dummy: 
[    0.378255] wmi: Mapper loaded
[    0.410105] audit: initializing netlink socket (disabled)
[    0.683863] i2c-core: driver [adp5520] using legacy suspend method
[    0.683865] i2c-core: driver [adp5520] using legacy resume method
[    0.686712] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.741864] device-mapper: multipath: version 1.2.0 loaded
[    0.741866] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.430543] ata7: SATA max UDMA/133 abar m8192@0xfeafe000 port 0xfeafe100 irq 16
[    1.905251] [drm] Internal thermal controller with fan control
[   22.078323] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   22.078787] Registered led device: rt73usb-phy0::radio
[   22.078804] Registered led device: rt73usb-phy0::assoc
[   22.078821] Registered led device: rt73usb-phy0::quality
[   22.079285] usbcore: registered new interface driver rt73usb
[   25.928103] Adding 4008180k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:4008180k 
[   28.027648] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.092357] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   38.156769] wlan0: authenticate with 00:1f:3f:0f:b8:94 (try 1)
[   38.159390] wlan0: authenticated
[   38.179007] wlan0: associate with 00:1f:3f:0f:b8:94 (try 1)
[   38.184396] wlan0: RX AssocResp from 00:1f:3f:0f:b8:94 (capab=0x411 status=0 aid=1)
[   38.184399] wlan0: associated
[   38.196566] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   48.850013] wlan0: no IPv6 routers present
[ 6219.037655] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
```

```
sudo iwlist scan
wlan0     Scan completed :
          Cell 01 - Address: 00:1F:3F:0F:B8:94
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"wlan1337"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000001674e291
                    Extra: Last beacon: 1490ms ago
                    IE: Unknown: 0008776C616E31333337
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD0A0800280101000200FF0F
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: 00:18:4D:85:F5:A2
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"D\xFCrni"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000107006b181
                    Extra: Last beacon: 640ms ago
                    IE: Unknown: 000544FC726E69
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
          Cell 03 - Address: 00:01:E3:D6:E3:53
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"private"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002597f601003
                    Extra: Last beacon: 1490ms ago
                    IE: Unknown: 000770726976617465
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 0706415420010D14
                    IE: Unknown: 2A0102
                    IE: Unknown: 32041224606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: DD0900037F0101000DFF7F
                    IE: Unknown: DD0C00037F020101500002A34000
                    IE: Unknown: DD1A00037F03010000000001E3D6E3530201E3D6E35364002C010D08
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
```

---

### Post by proxximity on 2011-05-13
The matching bugreport seems to be the following:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/773599](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/773599)

---

