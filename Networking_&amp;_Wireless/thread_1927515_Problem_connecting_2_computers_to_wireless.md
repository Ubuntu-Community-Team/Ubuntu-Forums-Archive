---
title: "Problem connecting 2 computers to wireless"
date: 2012-02-18
forum: Networking &amp; Wireless
---

### Post by Pulka on 2012-02-18
Hi.


A few days ago started to have a weird problem with my laptop and desktop computer.
I have them side by side, and the both find my home wireless network. But if i'm connected with one of them, the other can't connect. As soon as i disconnect one, the other is able to connect.

I have one more computer (windows) in my house, and that one connects ok. Also have an Ipad with no connections issue.

Any ideias of what be happening?

thank you

---

### Post by praseodym on 2012-02-18
Please show from both:

```
lspci -nnk | grep -iA2 net
lsmod
iwlist chan
iwconfig
```
and in general:
```
sudo iwlist scan
```
MAC-filter is off? Which mode does the router send (b, g, n)?

---

### Post by Pulka on 2012-02-18
MAC filter is on. How can i check the mode?

```

01:01.0 Network controller [0280]: Atheros Communications Inc. AR5008 Wireless Network Adapter [168c:0023] (rev 01)
	Subsystem: D-Link System Inc DWA-547 802.11n RangeBooster N 650 DeskTop Adapter [1186:3a6b]
	Kernel driver in use: ath9k
--
02:00.0 Ethernet controller [0200]: Atheros Communications L2 Fast Ethernet [1969:2048] (rev a0)
	Subsystem: ASUSTeK Computer Inc. Device [1043:8233]
	Kernel driver in use: atl2

```

**lsmod**

```
Module                  Size  Used by
xt_limit               12541  8 
xt_tcpudp              12531  7 
ipt_LOG                12783  8 
ipt_MASQUERADE         12663  0 
xt_DSCP                12549  0 
ipt_REJECT             12512  1 
nf_conntrack_irc       13138  0 
nf_conntrack_ftp       13183  0 
xt_state               12514  6 
vesafb                 13489  1 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
binfmt_misc            17292  1 
snd_hda_codec_hdmi     31426  1 
nvidia              10390874  40 
snd_hda_codec_realtek   254125  1 
snd_hda_intel          24262  3 
iptable_nat            13016  0 
nf_nat                 24958  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19084  9 iptable_nat,nf_nat
nf_conntrack           70103  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
snd_hda_codec          91859  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
iptable_mangle         12646  0 
iptable_filter         12706  1 
ip_tables              18106  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               21975  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
arc4                   12473  2 
snd_pcm                80435  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
ppdev                  12849  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ath9k                 112711  0 
mac80211              393421  1 ath9k
serio_raw              12990  0 
ath9k_common           13599  1 ath9k
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ath9k_hw              293933  2 ath9k,ath9k_common
ath                    19387  2 ath9k,ath9k_hw
asus_atk0110           17742  0 
cfg80211              172427  3 ath9k,mac80211,ath
parport_pc             32114  1 
snd                    55902  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
floppy                 60310  0 
usbhid                 41905  0 
hid                    77367  1 usbhid
atl2                   27979  0 
```

**iwlist chan**

```
lo        no frequency information.

eth0      no frequency information.

wlan0     13 channels in total; available frequencies :
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
          Current Frequency:2.422 GHz (Channel 3)
```

**iwconfig**

```
wlan0     IEEE 802.11bgn  ESSID:"ZONDJxxx"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:26:5B:4A:66:xx  
          Bit Rate=39 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=32/70  Signal level=-78 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3  Invalid misc:166   Missed beacon:0

```

**sudo iwlist scan**

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1F:9F:FE:61:0A
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"MEO-FE610A"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000b4cea90f3a2
                    Extra: Last beacon: 168ms ago
                    IE: Unknown: 000A4D454F2D464536313041
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0102
                    IE: Unknown: 2F0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001300000000000000000000000000000000000000
                    IE: Unknown: DD7E0050F204104A0001101044000102103B00010310470010DC822B435A835835837727E2E148E2031021000754484F4D534F4E1023000A54686F6D736F6E205447102400043738346E104200093130323354544A52361054000800060050F20400011011000E54686F6D736F6E2054473738346E100800020084103C000100
                    IE: Unknown: DD09001018020000050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101080003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C331C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001300000000000000000000000000000000000000
          Cell 02 - Address: 00:05:CA:8B:B6:48
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"ZON-B640"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000291c29f2f
                    Extra: Last beacon: 124ms ago
                    IE: Unknown: 00085A4F4E2D42363430
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010D
                    IE: Unknown: 2A0100
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 2D1A8C0117FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160D000400000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0501001A127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: DD1E00904C338C0117FFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340D000400000000000000000000000000000000000000
                    IE: Unknown: DD9D0050F204104A0001101044000102103B00010310470010BC329E001DD811B286010005CA8BB6481021001852616C696E6B20546563686E6F6C6F67792C20436F72702E1023001C52616C696E6B20576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F20400011011000952616C696E6B415053100800020084103C000101
          Cell 03 - Address: 00:05:CA:8B:B6:49
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:off
                    ESSID:"FON_ZON_FREE_INTERNET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000291c2a239
                    Extra: Last beacon: 124ms ago
                    IE: Unknown: 0015464F4E5F5A4F4E5F465245455F494E5445524E4554
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010D
                    IE: Unknown: 2A0100
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 2D1A8C0117FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160D000400000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0501001A127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: DD1E00904C338C0117FFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340D000400000000000000000000000000000000000000
          Cell 04 - Address: 90:84:0D:E0:82:7B
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"Discovercity's Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000061c6460160
                    Extra: Last beacon: 788ms ago
                    IE: Unknown: 0016446973636F766572636974792773204E6574776F726B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 0706505420010D1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AAC4117FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001100000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0700039301710320
                    IE: Unknown: DD070017F203020180
                    IE: Unknown: DD0E0017F2070001010690840DE0827B
          Cell 05 - Address: 00:24:17:07:D3:C4
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"TR3S Lisboa"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000631ae156f1
                    Extra: Last beacon: 792ms ago
                    IE: Unknown: 000B54523353204C6973626F61
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD7C0050F204104A0001101044000102103B0001031047001011E7C4C7382F5E258BBB448B42257F8D1021000754484F4D534F4E1023000A54686F6D736F6E2054471024000337383410420009303930314E543132421054000800060050F20400011011000D54686F6D736F6E205447373834100800020084103C000100
                    IE: Unknown: DD09001018020100040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101080003A4000027A4000042435E0062322F00
          Cell 06 - Address: 00:26:5B:4A:66:89
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:"FON_ZON_FREE_INTERNET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000022856719e4
                    Extra: Last beacon: 672ms ago
                    IE: Unknown: 0015464F4E5F5A4F4E5F465245455F494E5445524E4554
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030103
                    IE: Unknown: 2A0100
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 2D1A8C0117FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1603030700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B050300B7127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
          Cell 07 - Address: 00:26:5B:4A:66:88
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000022856709b3
                    Extra: Last beacon: 676ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030103
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 050402030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A8C0117FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1603030700000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B050300B7127A
                    IE: Unknown: DD07000C4300000000
          Cell 08 - Address: 00:26:5B:4A:66:88
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"ZONDJEDxx"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000022642d8722
                    Extra: Last beacon: 558120ms ago
                    IE: Unknown: 00095A4F4E444A45444A45
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030103
                    IE: Unknown: 2A0100
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 2D1A8C0117FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1603030700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05030056127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
          Cell 09 - Address: C0:D0:44:43:FB:77
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"SONAECOM_FB76"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000124b71ed934
                    Extra: Last beacon: 508ms ago
                    IE: Unknown: 000D534F4E4145434F4D5F46423736
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0000000
          Cell 10 - Address: 00:0F:66:ED:E2:D9
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"PBAMWLAN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000124b8228873
                    Extra: Last beacon: 508ms ago
                    IE: Unknown: 00085042414D574C414E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD050010180101
          Cell 11 - Address: 00:1E:8C:2C:00:46
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"AMC1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000089f2bdfbd0
                    Extra: Last beacon: 448ms ago
                    IE: Unknown: 0004414D4331
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030107
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020004
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: 00:05:CA:90:FA:89
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:off
                    ESSID:"FON_ZON_FREE_INTERNET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000019728dc6f
                    Extra: Last beacon: 408ms ago
                    IE: Unknown: 0015464F4E5F5A4F4E5F465245455F494E5445524E4554
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030108
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 050400030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A8C0117FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1608000000000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000022127A
                    IE: Unknown: DD1E00904C338C0117FFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3408000000000000000000000000000000000000000000
                    IE: Unknown: DD07000C4300000000

```

---

### Post by praseodym on 2012-02-18
Remove the iptables (firewall) and deactivate the hardware encryption of the driver ath9k:

```
sudo apt-get remove --purge ufw gufw
sudo iptables -t filter -n -L -v
sudo iptables -F
sudo iptables -X
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
Did you setup an Ad-Hoc network? If yes, remove (not edit) the wireless profile and setup a new one

---

### Post by Pulka on 2012-02-18
thank you for your help, but what are the consequences of disabling ip tables and removing hardware encryption?

For a newbie it sounds like i'm reducing my computer security.

sorry for my question

---

### Post by praseodym on 2012-02-18
The removing of the iptables resets your computer to default, so you can try it again ;-)

Disabling the hardware encryption does not reduce the security of the software encryption (WPA/WPA2, etc).

---

### Post by Pulka on 2012-02-18
> **praseodym said:**
> Remove the iptables (firewall) and deactivate the hardware encryption of the driver ath9k:

```
sudo apt-get remove --purge ufw gufw
sudo iptables -t filter -n -L -v
sudo iptables -F
sudo iptables -X
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
Did you setup an Ad-Hoc network? If yes, remove (not edit) the wireless profile and setup a new one

it's not set as an ad-hoc network. Did this on one of the computer. Should i do it on the other one?

---

### Post by praseodym on 2012-02-18
The one with the driver ath9k and the Atheros card (outputs above!)

---

### Post by Pulka on 2012-02-18
ok...thank your for your help.

all computers are connected to the internet. A little slow though.

thanks again

---

