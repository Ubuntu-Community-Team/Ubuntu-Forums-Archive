---
title: "I can see my home network, but cannot connect to it"
date: 2010-12-27
forum: Networking &amp; Wireless
---

### Post by Lince1 on 2010-12-27
Every time I restart my computer I get a dialogue asking information about my home network.
I have tried several combinations of the drop-downs, but nothing seems to work, I've never been able to connect to my wireless network.
Please advise.
Tech info follows:

Toshiba A65 - S126

Ubuntu 9.10
                - the Karmic Koala 

$ uname -mr
2.6.31-22-generic i686

$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.


02:04.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
        Subsystem: Askey Computer Corp. Device 7064
        Flags: bus master, medium devsel, latency 168, IRQ 17
        Memory at d0010000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ath5k
        Kernel modules: ath5k


$ iwconfig wlan0
wlan0     IEEE 802.11bg  Mode:Managed  Frequency:2.437 GHz  
          Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
pcmcia                 36808  0 
arc4                    1660  2 
ecb                     2524  2 
joydev                 10240  0 
snd_atiixp             15720  2 
snd_atiixp_modem       11940  0 
snd_ac97_codec        101216  2 snd_atiixp,snd_atiixp_modem
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  4 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
iptable_filter          3100  0 
snd_seq_oss            28608  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
ppdev                   6688  0 
psmouse                57332  0 
serio_raw               5280  0 
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59236  15 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           24296  1 
rsrc_nonstatic         11644  1 yenta_socket
pcmcia_core            36592  3 pcmcia,yenta_socket,rsrc_nonstatic
ath5k                 124772  0 
mac80211              181140  1 ath5k
led_class               4096  1 ath5k
ath                     8060  1 ath5k
cfg80211               93052  3 ath5k,mac80211,ath
parport_pc             31940  1 
i2c_piix4               9932  0 
shpchp                 32272  0 
soundcore               7264  1 snd
snd_page_alloc          9156  3 snd_atiixp,snd_atiixp_modem,snd_pcm
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
radeon                636000  2 
ttm                    36212  1 radeon
drm                   160096  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
8139too                22620  0 
8139cp                 19260  0 
mii                     5212  2 8139too,8139cp
ati_agp                 6760  1 
agpgart                34988  3 ttm,drm,ati_agp
video                  19380  0 
output                  2780  1 video

$ dmesg | grep "wlan0"
[   24.971236] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  191.212115] wlan0: authenticate with AP 00:0f:66:96:c0:1e
[  191.232087] wlan0: authenticated
[  191.232098] wlan0: associate with AP 00:0f:66:96:c0:1e
[  191.239158] wlan0: RX AssocResp from 00:0f:66:96:c0:1e (capab=0x411 status=0 aid=2)
[  191.239167] wlan0: associated
[  191.246334] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  201.247201] wlan0: disassociating by local choice (reason=3)
[  201.556036] wlan0: no IPv6 routers present
[  202.284138] wlan0: authenticate with AP 00:0f:66:96:c0:1e
[  202.286958] wlan0: authenticated
[  202.286971] wlan0: associate with AP 00:0f:66:96:c0:1e
[  202.292579] wlan0: RX AssocResp from 00:0f:66:96:c0:1e (capab=0x411 status=0 aid=2)
[  202.292588] wlan0: associated
[  212.301752] wlan0: disassociating by local choice (reason=3)
[  213.300137] wlan0: authenticate with AP 00:0f:66:96:c0:1e
[  213.304407] wlan0: authenticated
[  213.304418] wlan0: associate with AP 00:0f:66:96:c0:1e
[  213.306991] wlan0: RX AssocResp from 00:0f:66:96:c0:1e (capab=0x411 status=0 aid=2)
[  213.307000] wlan0: associated
[  223.313731] wlan0: disassociating by local choice (reason=3)
[  224.305567] wlan0: authenticate with AP 00:0f:66:96:c0:1e
[  224.308686] wlan0: authenticated
[  224.308697] wlan0: associate with AP 00:0f:66:96:c0:1e
[  224.319346] wlan0: RX AssocResp from 00:0f:66:96:c0:1e (capab=0x411 status=0 aid=2)
[  224.319355] wlan0: associated
[  234.321750] wlan0: disassociating by local choice (reason=3)
[  235.333485] wlan0: authenticate with AP 00:0f:66:96:c0:1e
[  235.340962] wlan0: authenticated
[  235.340974] wlan0: associate with AP 00:0f:66:96:c0:1e
[  235.347213] wlan0: RX AssocResp from 00:0f:66:96:c0:1e (capab=0x411 status=0 aid=2)
[  235.347223] wlan0: associated
[  245.349942] wlan0: disassociating by local choice (reason=3)
[  246.369452] wlan0: authenticate with AP 00:0f:66:96:c0:1e
[  246.380774] wlan0: authenticated
[  246.380786] wlan0: associate with AP 00:0f:66:96:c0:1e
[  246.384260] wlan0: RX AssocResp from 00:0f:66:96:c0:1e (capab=0x411 status=0 aid=2)
[  246.384269] wlan0: associated
[  250.439883] wlan0: disassociating by local choice (reason=3)
[  411.956605] wlan0: authenticate with AP 00:0f:66:96:c0:1e
[  411.960409] wlan0: authenticated
[  411.960421] wlan0: associate with AP 00:0f:66:96:c0:1e
[  411.964503] wlan0: RX AssocResp from 00:0f:66:96:c0:1e (capab=0x411 status=0 aid=2)
[  411.964513] wlan0: associated
[  421.968807] wlan0: disassociating by local choice (reason=3)
[  428.952130] wlan0: authenticate with AP 00:0f:66:96:c0:1e
[  428.954566] wlan0: authenticated
[  428.954578] wlan0: associate with AP 00:0f:66:96:c0:1e
[  428.960099] wlan0: RX AssocResp from 00:0f:66:96:c0:1e (capab=0x411 status=0 aid=2)
[  428.960108] wlan0: associated
[  438.963483] wlan0: disassociating by local choice (reason=3)
[  440.028746] wlan0: authenticate with AP 00:0f:66:96:c0:1e
[  440.035399] wlan0: authenticated
[  440.035411] wlan0: associate with AP 00:0f:66:96:c0:1e
[  440.038808] wlan0: RX AssocResp from 00:0f:66:96:c0:1e (capab=0x411 status=0 aid=2)
[  440.038818] wlan0: associated
[  450.042859] wlan0: disassociating by local choice (reason=3)
[  451.080136] wlan0: direct probe to AP 00:0f:66:96:c0:1e try 1
[  451.280078] wlan0: direct probe to AP 00:0f:66:96:c0:1e try 2
[  451.281809] wlan0 direct probe responded
[  451.281820] wlan0: authenticate with AP 00:0f:66:96:c0:1e
[  451.285663] wlan0: authenticated
[  451.285674] wlan0: associate with AP 00:0f:66:96:c0:1e
[  451.288475] wlan0: RX AssocResp from 00:0f:66:96:c0:1e (capab=0x411 status=0 aid=2)
[  451.288484] wlan0: associated
[  461.291750] wlan0: disassociating by local choice (reason=3)
[  462.336136] wlan0: authenticate with AP 00:0f:66:96:c0:1e
[  462.343426] wlan0: authenticated
[  462.343438] wlan0: associate with AP 00:0f:66:96:c0:1e
[  462.352099] wlan0: RX AssocResp from 00:0f:66:96:c0:1e (capab=0x411 status=0 aid=2)
[  462.352108] wlan0: associated
[  471.448999] wlan0: disassociating by local choice (reason=3)

$ sudo lshw -C network 
  *-network:0             
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: wmaster0
       version: 01
       serial: 00:90:96:bc:66:8f
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:d0010000-d001ffff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:02:07.0
       logical name: eth0
       version: 10
       serial: 00:a0:d1:dc:b6:d2
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half ip=192.168.1.106 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:18 ioport:a000(size=256) memory:d0000000-d00000ff

$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0F:66:96:C0:1E
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"homenet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000ef2a7717f
                    Extra: Last beacon: 8464ms ago
                    IE: Unknown: 0007686F6D656E6574
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 0406000200000000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
          Cell 02 - Address: 30:37:A6:A5:FB:01
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000004d00a1eac3f
                    Extra: Last beacon: 8892ms ago
                    IE: Unknown: 000100
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1A
                    IE: Unknown: 0B0500005A0000
                    IE: Unknown: 2A0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 851E10008F000F00FF0359004D634375746368656F6E5F48696E650000000030
                    IE: Unknown: 9606004096001A00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961401
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: 34:EF:44:89:63:D1
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"2WIRE928"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000004b963f61181
                    Extra: Last beacon: 7960ms ago
                    IE: Unknown: 00083257495245393238
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0102
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 04 - Address: 28:93:FE:24:0E:03
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=13/70  Signal level=-97 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000016a34de6be9
                    Extra: Last beacon: 8808ms ago
                    IE: Unknown: 000100
                    IE: Unknown: 010882040B0C12161824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1A
                    IE: Unknown: 0B050400730000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 851E0A008F000F00FF035900537479676C65725F524150000000000004000030
                    IE: Unknown: 9606004096001A00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961401
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 05 - Address: 30:37:A6:A5:FB:02
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:off
                    ESSID:"CitywideWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000004d00a26ebd9
                    Extra: Last beacon: 8376ms ago
                    IE: Unknown: 000C436974797769646557694669
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1A
                    IE: Unknown: 0B0500005A0000
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: 851E10008F000F00FF0359004D634375746368656F6E5F48696E650000000030
                    IE: Unknown: 9606004096001A00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 06 - Address: 30:37:A6:A4:D1:02
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key:off
                    ESSID:"CitywideWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002a707f65978
                    Extra: Last beacon: 8384ms ago
                    IE: Unknown: 000C436974797769646557694669
                    IE: Unknown: 010882040B0C12161824
                    IE: Unknown: 030106
                    IE: Unknown: 050700010000000000
                    IE: Unknown: 0706555320010B1A
                    IE: Unknown: 0B0501009A0000
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: 851E1A008F000F00FF0359004D634375746368656F6E5F576F6F640001000030
                    IE: Unknown: 9606004096001A00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 07 - Address: 30:37:A6:A4:D1:06
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002a707f65978
                    Extra: Last beacon: 8372ms ago
                    IE: Unknown: 000100
                    IE: Unknown: 010882040B0C12161824
                    IE: Unknown: 030106
                    IE: Unknown: 050700010000000000
                    IE: Unknown: 0706555320010B1A
                    IE: Unknown: 0B050100930000
                    IE: Unknown: 2A0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 32043048606C
                    IE: Unknown: 851E1A008F000F00FF0359004D634375746368656F6E5F576F6F640001000030
                    IE: Unknown: 9606004096001A00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961401
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 08 - Address: 00:14:A5:88:5F:5A
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=14/70  Signal level=-96 dBm  
                    Encryption key:on
                    ESSID:"Motorola8a4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000afe164187
                    Extra: Last beacon: 8888ms ago
                    IE: Unknown: 000B4D6F746F726F6C61386134
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD050010180102
          Cell 09 - Address: 00:1C:10:37:39:44
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"overlord"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000009b556e186
                    Extra: Last beacon: 8372ms ago
                    IE: Unknown: 00086F7665726C6F7264
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180203F4000000
          Cell 10 - Address: 00:1D:7E:1D:3B:A3
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"garden"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000011db9771183
                    Extra: Last beacon: 8404ms ago
                    IE: Unknown: 000667617264656E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F4000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: 00:22:6B:55:A1:E3
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"74687HOME"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Unknown/bug
                    Extra:tsf=000000c768877144
                    Extra: Last beacon: 8420ms ago
                    IE: Unknown: 00093734363837484F4D45
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD270050F204104A0001101044000102104700102880288028801880A88000226B55A1E3103C000101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1606000100000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33EC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3406000100000000000000000000000000000000000000
                    IE: Unknown: DD07000C4307000000
          Cell 12 - Address: 30:37:A6:A4:D1:00
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:off
                    ESSID:"HighSpeedAir"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002a707f65d76
                    Extra: Last beacon: 8408ms ago
                    IE: Unknown: 000C486967685370656564416972
                    IE: Unknown: 010882040B0C12161824
                    IE: Unknown: 030106
                    IE: Unknown: 050700010000000000
                    IE: Unknown: 0706555320010B1A
                    IE: Unknown: 0B050100930000
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: 851E1A008F000F00FF0359004D634375746368656F6E5F576F6F640001000030
                    IE: Unknown: 9606004096001A00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 13 - Address: 30:37:A6:A5:FB:04
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000004d00a26a191
                    Extra: Last beacon: 8408ms ago
                    IE: Unknown: 000100
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1A
                    IE: Unknown: 0B0500005A0000
                    IE: Unknown: 2A0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 851E10008F000F00FF0359004D634375746368656F6E5F48696E650000000030
                    IE: Unknown: 9606004096001A00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961401
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 14 - Address: 00:26:50:B4:BA:21
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key:on
                    ESSID:"2WIRE287"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000023cdf6d1181
                    Extra: Last beacon: 8008ms ago
                    IE: Unknown: 00083257495245323837
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C

---

