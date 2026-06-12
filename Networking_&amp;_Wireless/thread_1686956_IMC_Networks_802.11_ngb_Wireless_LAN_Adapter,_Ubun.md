---
title: "IMC Networks 802.11 n/g/b Wireless LAN Adapter, Ubuntu 10.10, Medion Akoya P7700"
date: 2011-02-13
forum: Networking &amp; Wireless
---

### Post by DrRavenwood on 2011-02-13
Hey, I'm quite new here and to Linux, so hope u'all can help up out...

I'm having trouble with getting my wireless lan card working with encryptions. I've read like a million posts around this forum and other places on the web, but I can't find anyone with my specific build or lan card.

I've tried to connect to the wlan without encryptions, that works. Turning on any kind of encryption and configuring it with my wlan card in the "network connections" menu makes me loss the connection, it keeps asking 4 the Password, and I'm sure it's the right one I'm using...

anyways, I took my time checking u're ticket guide, so here's what it said.

$ lsusb - got me this

Bus 001 Device 003: ID 13d3:3247 IMC Networks 802.11 n/g/b Wireless LAN Adapter

If u need more than that, I'll post the rest of it...

$ ifconfig
wlan0     Link encap:Ethernet  HWaddr 00:15:af:72:54:a1  
          inet6 addr: fe80::215:afff:fe72:54a1/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:339 (339.0 B)  TX bytes:3427 (3.4 KB)

$ iwconfig
wlan0     IEEE 802.11bgn  ESSID:"raven"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=9 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

$ lsmod
Module                  Size  Used by
nls_utf8                1069  1 
udf                    79366  1 
binfmt_misc             6599  1 
parport_pc             26378  0 
ppdev                   5556  0 
nvidia               9331115  38 
snd_hda_codec_realtek   218492  1 
rt2870sta             406818  0 
snd_hda_intel          22267  4 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
arc4                    1165  2 
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71603  3 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
rt2800usb               8367  0 
rt2800lib              28897  1 rt2800usb
rt2x00usb               9779  2 rt2800usb,rt2800lib
rt2x00lib              27307  2 rt2800lib,rt2x00usb
led_class               2633  1 rt2x00lib
mac80211              231959  2 rt2x00usb,rt2x00lib
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              144694  2 rt2x00lib,mac80211
joydev                  8767  0 
crc_ccitt               1351  2 rt2870sta,rt2800usb
snd                    49038  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              26926  0 
psmouse                59033  0 
serio_raw               4022  0 
soundcore                880  1 snd
snd_page_alloc          7216  2 snd_hda_intel,snd_pcm
agpgart                32075  2 nvidia,intel_agp
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
hid_logitech            8971  0 
ff_memless              4393  1 hid_logitech
usbhid                 36978  1 hid_logitech
hid                    67742  2 hid_logitech,usbhid
usb_storage            40204  2 
ahci                   19198  4 
firewire_ohci          21554  0 
firewire_core          46675  1 firewire_ohci
libahci                21792  1 ahci
crc_itu_t               1383  2 udf,firewire_core
e1000e                133436  0

$ dmesg
6 21:45 (103c)
[   42.574901] wlan0: authenticate with 00:1b:11:9a:6d:1e (try 1)
[   42.576650] wlan0: authenticated
[   42.577389] wlan0: associate with 00:1b:11:9a:6d:1e (try 1)
[   42.579520] wlan0: RX AssocResp from 00:1b:11:9a:6d:1e (capab=0x431 status=0 aid=3)
[   42.579523] wlan0: associated
[   42.588091] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   47.088015] wlan0: disassociated from 00:1b:11:9a:6d:1e (Reason: 3)
[   47.120815] wlan0: deauthenticating from 00:1b:11:9a:6d:1e by local choice (reason=3)
[   47.120853] cfg80211: All devices are disconnected, going to restore regulatory settings
[   47.120857] cfg80211: Restoring regulatory settings
[   47.120860] cfg80211: Calling CRDA to update world regulatory domain
[   47.124262] cfg80211: World regulatory domain updated:
[   47.124265]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   47.124268]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   47.124270]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   47.124272]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   47.124275]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   47.124277]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   48.529956] wlan0: authenticate with 00:1b:11:9a:6d:1e (try 1)
[   48.532967] wlan0: authenticated
[   48.534209] wlan0: associate with 00:1b:11:9a:6d:1e (try 1)
[   48.536094] wlan0: RX AssocResp from 00:1b:11:9a:6d:1e (capab=0x431 status=0 aid=3)
[   48.536097] wlan0: associated
[   52.238563] wlan0: disassociated from 00:1b:11:9a:6d:1e (Reason: 3)
[   52.269809] wlan0: deauthenticating from 00:1b:11:9a:6d:1e by local choice (reason=3)
[   52.269836] cfg80211: All devices are disconnected, going to restore regulatory settings
[   52.269840] cfg80211: Restoring regulatory settings
[   52.269843] cfg80211: Calling CRDA to update world regulatory domain
[   52.273119] cfg80211: World regulatory domain updated:
[   52.273122]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   52.273124]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   52.273127]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   52.273129]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   52.273131]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   52.273133]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   52.609004] wlan0: no IPv6 routers present
[   53.674839] wlan0: authenticate with 00:1b:11:9a:6d:1e (try 1)
[   53.677710] wlan0: authenticated
[   53.677726] wlan0: associate with 00:1b:11:9a:6d:1e (try 1)
[   53.680954] wlan0: RX AssocResp from 00:1b:11:9a:6d:1e (capab=0x431 status=0 aid=3)
[   53.680957] wlan0: associated
[   57.388061] wlan0: disassociated from 00:1b:11:9a:6d:1e (Reason: 3)
[   57.420807] wlan0: deauthenticating from 00:1b:11:9a:6d:1e by local choice (reason=3)
[   57.420843] cfg80211: All devices are disconnected, going to restore regulatory settings
[   57.420847] cfg80211: Restoring regulatory settings
[   57.420850] cfg80211: Calling CRDA to update world regulatory domain
[   57.424062] cfg80211: World regulatory domain updated:
[   57.424065]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   57.424068]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   57.424070]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   57.424073]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   57.424075]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   57.424077]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   58.831575] wlan0: authenticate with 00:1b:11:9a:6d:1e (try 1)
[   59.028016] wlan0: authenticate with 00:1b:11:9a:6d:1e (try 2)
[   59.228015] wlan0: authenticate with 00:1b:11:9a:6d:1e (try 3)
[   59.428013] wlan0: authentication with 00:1b:11:9a:6d:1e timed out

$ sudo lshw -C network
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:6
       logical name: wlan0
       serial: 00:15:af:72:54:a1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=2.6.35-25-generic-pae firmware=N/A link=no multicast=yes wireless=IEEE 802.11bgn

$ iwlist scan
wlan0     Scan completed :
          Cell 01 - Address: CE:13:22:DA:7B:47
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=0 dBm  
                    Encryption key:on
                    ESSID:"raven"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 79692ms ago
                    IE: Unknown: 0005726176656E
                    IE: Unknown: 010882840B160C121824
                    IE: Unknown: 030101
                    IE: Unknown: 06020000
                    IE: Unknown: 32043048606C
          Cell 02 - Address: 00:1F:33:C2:F2:54
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-189 dBm  
                    Encryption key:off
                    ESSID:"Airport Test"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a124e31183
                    Extra: Last beacon: 200ms ago
                    IE: Unknown: 000C416972706F72742054657374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050402030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: 00:19:70:14:D7:9A
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-186 dBm  
                    Encryption key:on
                    ESSID:"TDC-4774"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007085903984
                    Extra: Last beacon: 188ms ago
                    IE: Unknown: 00085444432D34373734
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 200100
                    IE: Unknown: 2A0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: 07064E4120010D14
                    IE: Unknown: DD2C0050F204104A0001101044000102105700010010470010565AA94967C14C0EAA8FF349E6F59311103C000101

$ uname -mr
2.6.35-25-generic-pae i686

$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...
Ignoring unknown interface eth0=eth0.
Ignoring unknown interface wlan0=wlan0. 
[ OK ]


Anyways, I hope u can help me solve my problem. As I said before I'm quite new to Ubuntu, and it's killing me I can't figure this out myself...

Thanks in advance...

---

### Post by DrRavenwood on 2011-02-13
Geez...

After doing all this now it suddenly works...

Sry 4 the bother :S I'll return if it dies again...

---

### Post by DrRavenwood on 2011-02-13
Okay, this is sort of getting annoyin'... Now it doesn't work again...

I tried to restart the computer, which doesn't help, so back to square one :(

Any ideas ??

---

### Post by DrRavenwood on 2011-02-14
Think I solved it by turning of ipv6...

and since I couldn't do it in /etc/modprobe.d/aliases - since this doesn't exist...

I followed this guide - 

[http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html](http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html)

works on ubuntu 10.10 aswell...

---

