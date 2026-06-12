---
title: "TP-Link TL-WN781N -  So Slow"
date: 2011-11-12
forum: Networking &amp; Wireless
---

### Post by Rodney9 on 2011-11-12
Hello,

I have a TP-Link TL-WN781N Wireless 150M Lite-N PCI Express Adapter, it connects, but never above 50% and it is just so slow on the internet, makes me think I'm back on dial-up.

I am only 20 feet away from the router in another room. 

I am using Lubuntu 11.10 64bit on my desktop.

I have added some info below.

Thanks for any clues or ideas.

Rodney

---

### Post by Rodney9 on 2011-11-13
TP-Link TL-WN781N -  So Slow

I followed the commands from the other post, hopefully they are helpful.

```
$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux rodney-P5Q-PRO 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux


lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Atheros Communications AR8121/AR8113/AR8114 Gigabit or Fast Ethernet [1969:1026] (rev b0)
	Subsystem: ASUSTeK Computer Inc. Device [1043:8226]
	Kernel driver in use: ATL1E
--
03:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: Atheros Communications Inc. Device [168c:30a1]
	Kernel driver in use: ath9k
```

```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"wlan-ap"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 40:61:86:9D:D5:83   
          Bit Rate=135 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=41/70  Signal level=-69 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:66  Invalid misc:5   Missed beacon:0



$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no



$ lsmod
Module                  Size  Used by
parport_pc             36962  0 
ppdev                  17113  0 
vesafb                 13809  1 
nvidia              11713772  30 
joydev                 17693  0 
usb_storage            57901  0 
uas                    18027  0 
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  1 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
arc4                   12529  2 
psmouse                73882  0 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
ath9k                 127538  0 
serio_raw              13166  0 
mac80211              310872  1 ath9k
asus_atk0110           18078  0 
snd                    68266  11 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath9k_common           13839  1 ath9k
ath9k_hw              312866  2 ath9k,ath9k_common
ath                    24067  2 ath9k,ath9k_hw
cfg80211              199587  3 ath9k,mac80211,ath
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
firewire_ohci          40722  0 
floppy                 70365  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
atl1e                  42080  0 
```


```
nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [wlan-ap] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        F8:D1:11:20:3E:02

  Capabilities:
    Speed:           150 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *wlan-ap:        Infra, 40:61:86:9D:D5:83, Freq 2412 MHz, Rate 54 Mb/s, Strength 60 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            ATL1E
  State:             unavailable
  Default:           no
  HW Address:        00:22:15:20:1B:3F

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


```


```
$ sudo iwlist scan
[sudo] password for rodney: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 40:61:86:9D:D5:83
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"wlan-ap"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000010e96d1b149
                    Extra: Last beacon: 716ms ago
                    IE: Unknown: 0007776C616E2D6170
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 2D1A6E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601050400000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0501000F127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706415520010D10
                    IE: Unknown: DD1E00904C336E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3401050400000000000000000000000000000000000000
          Cell 02 - Address: 00:26:18:10:79:53
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"OPTUSVB2001A"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000004a5d0f1c18e
                    Extra: Last beacon: 492ms ago
                    IE: Unknown: 000C4F5054555356423230303141
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180205F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
```


```
$ lsmod | grep wl

Gives Nothing
```


```
$ dmesg | egrep 'wl|firm|eth1'
[18713.162223] wlan0: deauthenticated from 40:61:86:9d:d5:83 (Reason: 3)
[18714.076390] wlan0: authenticate with 40:61:86:9d:d5:83 (try 1)
[18714.081588] wlan0: authenticated
[18714.099659] wlan0: associate with 40:61:86:9d:d5:83 (try 1)
[18714.108601] wlan0: RX ReassocResp from 40:61:86:9d:d5:83 (capab=0x411 status=0 aid=1)
[18714.108605] wlan0: associated
[19014.408120] wlan0: deauthenticated from 40:61:86:9d:d5:83 (Reason: 3)
[19015.324422] wlan0: authenticate with 40:61:86:9d:d5:83 (try 1)
[19015.325979] wlan0: authenticated
[19015.344065] wlan0: associate with 40:61:86:9d:d5:83 (try 1)
[19015.351660] wlan0: RX ReassocResp from 40:61:86:9d:d5:83 (capab=0x411 status=0 aid=1)
[19015.351663] wlan0: associated
[19315.656098] wlan0: deauthenticated from 40:61:86:9d:d5:83 (Reason: 3)
[19316.580389] wlan0: authenticate with 40:61:86:9d:d5:83 (try 1)
[19316.582003] wlan0: authenticated
[19316.600089] wlan0: associate with 40:61:86:9d:d5:83 (try 1)
[19316.608063] wlan0: RX ReassocResp from 40:61:86:9d:d5:83 (capab=0x411 status=0 aid=1)
[19316.608067] wlan0: associated
[19616.903959] wlan0: deauthenticated from 40:61:86:9d:d5:83 (Reason: 3)
[19617.844525] wlan0: authenticate with 40:61:86:9d:d5:83 (try 1)
[19617.846024] wlan0: authenticated
[19617.864105] wlan0: associate with 40:61:86:9d:d5:83 (try 1)
[19617.873426] wlan0: RX ReassocResp from 40:61:86:9d:d5:83 (capab=0x411 status=0 aid=1)
[19617.873429] wlan0: associated
[19918.152906] wlan0: deauthenticated from 40:61:86:9d:d5:83 (Reason: 3)
[19919.076490] wlan0: authenticate with 40:61:86:9d:d5:83 (try 1)
[19919.078008] wlan0: authenticated
[19919.096204] wlan0: associate with 40:61:86:9d:d5:83 (try 1)
[19919.105506] wlan0: RX ReassocResp from 40:61:86:9d:d5:83 (capab=0x411 status=0 aid=1)
[19919.105510] wlan0: associated
[20219.401136] wlan0: deauthenticated from 40:61:86:9d:d5:83 (Reason: 3)
[20220.320422] wlan0: authenticate with 40:61:86:9d:d5:83 (try 1)
[20220.322024] wlan0: authenticated
[20220.340106] wlan0: associate with 40:61:86:9d:d5:83 (try 1)
[20220.347715] wlan0: RX ReassocResp from 40:61:86:9d:d5:83 (capab=0x411 status=0 aid=1)
[20220.347718] wlan0: associated
[20520.647446] wlan0: deauthenticated from 40:61:86:9d:d5:83 (Reason: 3)
[20521.560943] wlan0: authenticate with 40:61:86:9d:d5:83 (try 1)
[20521.562497] wlan0: authenticated
[20521.580598] wlan0: associate with 40:61:86:9d:d5:83 (try 1)
[20521.588413] wlan0: RX ReassocResp from 40:61:86:9d:d5:83 (capab=0x411 status=0 aid=1)
[20521.588416] wlan0: associated
[20821.895242] wlan0: deauthenticated from 40:61:86:9d:d5:83 (Reason: 3)
[20822.808435] wlan0: authenticate with 40:61:86:9d:d5:83 (try 1)
[20822.810031] wlan0: authenticated
[20822.828275] wlan0: associate with 40:61:86:9d:d5:83 (try 1)
[20822.836246] wlan0: RX ReassocResp from 40:61:86:9d:d5:83 (capab=0x411 status=0 aid=1)
[20822.836249] wlan0: associated
[21123.143116] wlan0: deauthenticated from 40:61:86:9d:d5:83 (Reason: 3)
[21124.076445] wlan0: authenticate with 40:61:86:9d:d5:83 (try 1)
[21124.077925] wlan0: authenticated
[21124.096034] wlan0: associate with 40:61:86:9d:d5:83 (try 1)
[21124.103947] wlan0: RX ReassocResp from 40:61:86:9d:d5:83 (capab=0x411 status=0 aid=1)
[21124.103951] wlan0: associated
[21424.391128] wlan0: deauthenticated from 40:61:86:9d:d5:83 (Reason: 3)
[21425.308387] wlan0: authenticate with 40:61:86:9d:d5:83 (try 1)
[21425.309894] wlan0: authenticated
[21425.327975] wlan0: associate with 40:61:86:9d:d5:83 (try 1)
[21425.335814] wlan0: RX ReassocResp from 40:61:86:9d:d5:83 (capab=0x411 status=0 aid=1)
[21425.335817] wlan0: associated
[21725.638878] wlan0: deauthenticated from 40:61:86:9d:d5:83 (Reason: 3)
[21726.564950] wlan0: authenticate with 40:61:86:9d:d5:83 (try 1)
[21726.566503] wlan0: authenticated
[21726.584943] wlan0: associate with 40:61:86:9d:d5:83 (try 1)
[21726.594302] wlan0: RX ReassocResp from 40:61:86:9d:d5:83 (capab=0x411 status=0 aid=1)
[21726.594305] wlan0: associated
[22026.886669] wlan0: deauthenticated from 40:61:86:9d:d5:83 (Reason: 3)
[22027.800423] wlan0: authenticate with 40:61:86:9d:d5:83 (try 1)
[22027.802023] wlan0: authenticated
[22027.820101] wlan0: associate with 40:61:86:9d:d5:83 (try 1)
[22027.828050] wlan0: RX ReassocResp from 40:61:86:9d:d5:83 (capab=0x411 status=0 aid=1)
[22027.828054] wlan0: associated
[22328.134578] wlan0: deauthenticated from 40:61:86:9d:d5:83 (Reason: 3)
[22329.056546] wlan0: authenticate with 40:61:86:9d:d5:83 (try 1)
[22329.058140] wlan0: authenticated
[22329.076212] wlan0: associate with 40:61:86:9d:d5:83 (try 1)
[22329.083863] wlan0: RX ReassocResp from 40:61:86:9d:d5:83 (capab=0x411 status=0 aid=1)
[22329.083867] wlan0: associated
[22629.382569] wlan0: deauthenticated from 40:61:86:9d:d5:83 (Reason: 3)
[22630.304631] wlan0: authenticate with 40:61:86:9d:d5:83 (try 1)
[22630.306233] wlan0: authenticated
[22630.324323] wlan0: associate with 40:61:86:9d:d5:83 (try 1)
[22630.332251] wlan0: RX ReassocResp from 40:61:86:9d:d5:83 (capab=0x411 status=0 aid=1)
[22630.332254] wlan0: associated
[22930.631828] wlan0: deauthenticated from 40:61:86:9d:d5:83 (Reason: 3)
[22931.544393] wlan0: authenticate with 40:61:86:9d:d5:83 (try 1)
[22931.546009] wlan0: authenticated
[22931.564147] wlan0: associate with 40:61:86:9d:d5:83 (try 1)
[22931.571968] wlan0: RX ReassocResp from 40:61:86:9d:d5:83 (capab=0x411 status=0 aid=1)
[22931.571971] wlan0: associated
[23231.879441] wlan0: deauthenticated from 40:61:86:9d:d5:83 (Reason: 3)
[23233.676372] wlan0: authenticate with 40:61:86:9d:d5:83 (try 1)
[23233.677985] wlan0: authenticated
[23233.696057] wlan0: associate with 40:61:86:9d:d5:83 (try 1)
[23233.703962] wlan0: RX ReassocResp from 40:61:86:9d:d5:83 (capab=0x411 status=0 aid=1)
[23233.703966] wlan0: associated
[23534.127068] wlan0: deauthenticated from 40:61:86:9d:d5:83 (Reason: 3)
[23535.041062] wlan0: authenticate with 40:61:86:9d:d5:83 (try 1)
[23535.043464] wlan0: authenticated
[23535.061546] wlan0: associate with 40:61:86:9d:d5:83 (try 1)
[23535.069441] wlan0: RX ReassocResp from 40:61:86:9d:d5:83 (capab=0x411 status=0 aid=1)
[23535.069445] wlan0: associated
[23835.374983] wlan0: deauthenticated from 40:61:86:9d:d5:83 (Reason: 3)
[23836.292378] wlan0: authenticate with 40:61:86:9d:d5:83 (try 1)
[23836.294142] wlan0: authenticated
[23836.312207] wlan0: associate with 40:61:86:9d:d5:83 (try 1)
[23836.321392] wlan0: RX ReassocResp from 40:61:86:9d:d5:83 (capab=0x411 status=0 aid=1)
[23836.321396] wlan0: associated
[24136.622874] wlan0: deauthenticated from 40:61:86:9d:d5:83 (Reason: 3)
[24137.540439] wlan0: authenticate with 40:61:86:9d:d5:83 (try 1)
[24137.541943] wlan0: authenticated
[24137.542351] wlan0: associate with 40:61:86:9d:d5:83 (try 1)
[24137.552591] wlan0: RX ReassocResp from 40:61:86:9d:d5:83 (capab=0x411 status=0 aid=1)
[24137.552595] wlan0: associated
[24437.870906] wlan0: deauthenticated from 40:61:86:9d:d5:83 (Reason: 3)
[24438.776483] wlan0: authenticate with 40:61:86:9d:d5:83 (try 1)
[24438.778059] wlan0: authenticated
[24438.796145] wlan0: associate with 40:61:86:9d:d5:83 (try 1)
[24438.804049] wlan0: RX ReassocResp from 40:61:86:9d:d5:83 (capab=0x411 status=0 aid=1)
[24438.804053] wlan0: associated
[24739.123109] wlan0: deauthenticated from 40:61:86:9d:d5:83 (Reason: 3)
[24740.044421] wlan0: authenticate with 40:61:86:9d:d5:83 (try 1)
[24740.046375] wlan0: authenticated
[24740.064474] wlan0: associate with 40:61:86:9d:d5:83 (try 1)
[24740.072360] wlan0: RX ReassocResp from 40:61:86:9d:d5:83 (capab=0x411 status=0 aid=1)
[24740.072364] wlan0: associated
[25040.367037] wlan0: deauthenticated from 40:61:86:9d:d5:83 (Reason: 3)
[25041.284558] wlan0: authenticate with 40:61:86:9d:d5:83 (try 1)
[25041.286062] wlan0: authenticated
[25041.304182] wlan0: associate with 40:61:86:9d:d5:83 (try 1)
[25041.313002] wlan0: RX ReassocResp from 40:61:86:9d:d5:83 (capab=0x411 status=0 aid=1)
[25041.313005] wlan0: associated
[25341.616132] wlan0: deauthenticated from 40:61:86:9d:d5:83 (Reason: 3)
[25342.536415] wlan0: authenticate with 40:61:86:9d:d5:83 (try 1)
[25342.538562] wlan0: authenticated
[25342.556671] wlan0: associate with 40:61:86:9d:d5:83 (try 1)
[25342.564558] wlan0: RX ReassocResp from 40:61:86:9d:d5:83 (capab=0x411 status=0 aid=1)
[25342.564561] wlan0: associated
[25642.863481] wlan0: deauthenticated from 40:61:86:9d:d5:83 (Reason: 3)
[25643.777059] wlan0: authenticate with 40:61:86:9d:d5:83 (try 1)
[25643.780187] wlan0: authenticated
[25643.798267] wlan0: associate with 40:61:86:9d:d5:83 (try 1)
[25643.806411] wlan0: RX ReassocResp from 40:61:86:9d:d5:83 (capab=0x411 status=0 aid=1)
[25643.806414] wlan0: associated
[25944.111831] wlan0: deauthenticated from 40:61:86:9d:d5:83 (Reason: 3)
[25945.028409] wlan0: authenticate with 40:61:86:9d:d5:83 (try 1)
[25945.029900] wlan0: authenticated
[25945.047963] wlan0: associate with 40:61:86:9d:d5:83 (try 1)
[25945.057380] wlan0: RX ReassocResp from 40:61:86:9d:d5:83 (capab=0x411 status=0 aid=1)
[25945.057383] wlan0: associated
[26245.360128] wlan0: deauthenticated from 40:61:86:9d:d5:83 (Reason: 3)
[26246.272472] wlan0: authenticate with 40:61:86:9d:d5:83 (try 1)
[26246.273982] wlan0: authenticated
[26246.292066] wlan0: associate with 40:61:86:9d:d5:83 (try 1)
[26246.301318] wlan0: RX ReassocResp from 40:61:86:9d:d5:83 (capab=0x411 status=0 aid=1)
[26246.301321] wlan0: associated
[26546.608302] wlan0: deauthenticated from 40:61:86:9d:d5:83 (Reason: 3)
[26547.516583] wlan0: authenticate with 40:61:86:9d:d5:83 (try 1)
[26547.518162] wlan0: authenticated
[26547.536261] wlan0: associate with 40:61:86:9d:d5:83 (try 1)
[26547.544111] wlan0: RX ReassocResp from 40:61:86:9d:d5:83 (capab=0x411 status=0 aid=1)
[26547.544115] wlan0: associated
[26847.856685] wlan0: deauthenticated from 40:61:86:9d:d5:83 (Reason: 3)
[26848.768398] wlan0: authenticate with 40:61:86:9d:d5:83 (try 1)
[26848.770133] wlan0: authenticated
[26848.788219] wlan0: associate with 40:61:86:9d:d5:83 (try 1)
[26848.796098] wlan0: RX ReassocResp from 40:61:86:9d:d5:83 (capab=0x411 status=0 aid=1)
[26848.796102] wlan0: associated
[27149.105408] wlan0: deauthenticated from 40:61:86:9d:d5:83 (Reason: 3)
[27150.012778] wlan0: authenticate with 40:61:86:9d:d5:83 (try 1)
[27150.014282] wlan0: authenticated
[27150.032449] wlan0: associate with 40:61:86:9d:d5:83 (try 1)
[27150.040366] wlan0: RX ReassocResp from 40:61:86:9d:d5:83 (capab=0x411 status=0 aid=1)
[27150.040370] wlan0: associated
[27450.353933] wlan0: deauthenticated from 40:61:86:9d:d5:83 (Reason: 3)
[27451.272387] wlan0: authenticate with 40:61:86:9d:d5:83 (try 1)
[27451.273917] wlan0: authenticated
[27451.291980] wlan0: associate with 40:61:86:9d:d5:83 (try 1)
[27451.304894] wlan0: RX ReassocResp from 40:61:86:9d:d5:83 (capab=0x411 status=0 aid=1)
[27451.304898] wlan0: associated
[27751.602315] wlan0: deauthenticated from 40:61:86:9d:d5:83 (Reason: 3)
[27752.512369] wlan0: authenticate with 40:61:86:9d:d5:83 (try 1)
[27752.513922] wlan0: authenticated
[27752.532006] wlan0: associate with 40:61:86:9d:d5:83 (try 1)
[27752.539972] wlan0: RX ReassocResp from 40:61:86:9d:d5:83 (capab=0x411 status=0 aid=1)
[27752.539976] wlan0: associated
[28052.850811] wlan0: deauthenticated from 40:61:86:9d:d5:83 (Reason: 3)
[28053.757083] wlan0: authenticate with 40:61:86:9d:d5:83 (try 1)
[28053.758594] wlan0: authenticated
[28053.758758] wlan0: associate with 40:61:86:9d:d5:83 (try 1)
[28053.766355] wlan0: RX ReassocResp from 40:61:86:9d:d5:83 (capab=0x411 status=0 aid=1)
[28053.766358] wlan0: associated
[28354.100765] wlan0: deauthenticated from 40:61:86:9d:d5:83 (Reason: 3)
[28355.024388] wlan0: authenticate with 40:61:86:9d:d5:83 (try 1)
[28355.025887] wlan0: authenticated
[28355.043945] wlan0: associate with 40:61:86:9d:d5:83 (try 1)
[28355.051822] wlan0: RX ReassocResp from 40:61:86:9d:d5:83 (capab=0x411 status=0 aid=1)
[28355.051825] wlan0: associated
[28655.347984] wlan0: deauthenticated from 40:61:86:9d:d5:83 (Reason: 3)
[28656.264760] wlan0: authenticate with 40:61:86:9d:d5:83 (try 1)
[28656.266316] wlan0: authenticated
[28656.266489] wlan0: associate with 40:61:86:9d:d5:83 (try 1)
[28656.274098] wlan0: RX ReassocResp from 40:61:86:9d:d5:83 (capab=0x411 status=0 aid=1)
[28656.274102] wlan0: associated
[28956.596615] wlan0: deauthenticated from 40:61:86:9d:d5:83 (Reason: 3)
[28957.504424] wlan0: authenticate with 40:61:86:9d:d5:83 (try 1)
[28957.505989] wlan0: authenticated
[28957.524074] wlan0: associate with 40:61:86:9d:d5:83 (try 1)
[28957.532229] wlan0: RX ReassocResp from 40:61:86:9d:d5:83 (capab=0x411 status=0 aid=1)
[28957.532233] wlan0: associated


```

```
$ sudo cat /var/log/syslog | grep -e wl -e firmware -e eth1 -e wpa -e etwork | tail -n55
[sudo] password for rodney: 
Nov 13 15:22:12 rodney-P5Q-PRO NetworkManager[896]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 13 15:22:12 rodney-P5Q-PRO wpa_supplicant[957]: Trying to associate with 40:61:86:9d:d5:83 (SSID='wlan-ap' freq=2412 MHz)
Nov 13 15:22:12 rodney-P5Q-PRO kernel: [28355.024388] wlan0: authenticate with 40:61:86:9d:d5:83 (try 1)
Nov 13 15:22:12 rodney-P5Q-PRO kernel: [28355.025887] wlan0: authenticated
Nov 13 15:22:12 rodney-P5Q-PRO NetworkManager[896]: <info> (wlan0): supplicant interface state: authenticating -> associating
Nov 13 15:22:13 rodney-P5Q-PRO kernel: [28355.043945] wlan0: associate with 40:61:86:9d:d5:83 (try 1)
Nov 13 15:22:13 rodney-P5Q-PRO kernel: [28355.051822] wlan0: RX ReassocResp from 40:61:86:9d:d5:83 (capab=0x411 status=0 aid=1)
Nov 13 15:22:13 rodney-P5Q-PRO kernel: [28355.051825] wlan0: associated
Nov 13 15:22:13 rodney-P5Q-PRO wpa_supplicant[957]: Associated with 40:61:86:9d:d5:83
Nov 13 15:22:13 rodney-P5Q-PRO NetworkManager[896]: <info> (wlan0): supplicant interface state: associating -> associated
Nov 13 15:22:13 rodney-P5Q-PRO wpa_supplicant[957]: WPA: Key negotiation completed with 40:61:86:9d:d5:83 [PTK=TKIP GTK=TKIP]
Nov 13 15:22:13 rodney-P5Q-PRO wpa_supplicant[957]: CTRL-EVENT-CONNECTED - Connection to 40:61:86:9d:d5:83 completed (reauth) [id=0 id_str=]
Nov 13 15:22:13 rodney-P5Q-PRO NetworkManager[896]: <info> (wlan0): supplicant interface state: associated -> completed
Nov 13 15:27:13 rodney-P5Q-PRO kernel: [28655.347984] wlan0: deauthenticated from 40:61:86:9d:d5:83 (Reason: 3)
Nov 13 15:27:13 rodney-P5Q-PRO wpa_supplicant[957]: CTRL-EVENT-DISCONNECTED bssid=40:61:86:9d:d5:83 reason=3
Nov 13 15:27:13 rodney-P5Q-PRO NetworkManager[896]: <info> (wlan0): supplicant interface state: completed -> disconnected
Nov 13 15:27:13 rodney-P5Q-PRO NetworkManager[896]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 13 15:27:14 rodney-P5Q-PRO wpa_supplicant[957]: Trying to authenticate with 40:61:86:9d:d5:83 (SSID='wlan-ap' freq=2412 MHz)
Nov 13 15:27:14 rodney-P5Q-PRO NetworkManager[896]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 13 15:27:14 rodney-P5Q-PRO wpa_supplicant[957]: Trying to associate with 40:61:86:9d:d5:83 (SSID='wlan-ap' freq=2412 MHz)
Nov 13 15:27:14 rodney-P5Q-PRO kernel: [28656.264760] wlan0: authenticate with 40:61:86:9d:d5:83 (try 1)
Nov 13 15:27:14 rodney-P5Q-PRO kernel: [28656.266316] wlan0: authenticated
Nov 13 15:27:14 rodney-P5Q-PRO kernel: [28656.266489] wlan0: associate with 40:61:86:9d:d5:83 (try 1)
Nov 13 15:27:14 rodney-P5Q-PRO NetworkManager[896]: <info> (wlan0): supplicant interface state: authenticating -> associating
Nov 13 15:27:14 rodney-P5Q-PRO kernel: [28656.274098] wlan0: RX ReassocResp from 40:61:86:9d:d5:83 (capab=0x411 status=0 aid=1)
Nov 13 15:27:14 rodney-P5Q-PRO kernel: [28656.274102] wlan0: associated
Nov 13 15:27:14 rodney-P5Q-PRO wpa_supplicant[957]: Associated with 40:61:86:9d:d5:83
Nov 13 15:27:14 rodney-P5Q-PRO NetworkManager[896]: <info> (wlan0): supplicant interface state: associating -> associated
Nov 13 15:27:14 rodney-P5Q-PRO wpa_supplicant[957]: WPA: Key negotiation completed with 40:61:86:9d:d5:83 [PTK=TKIP GTK=TKIP]
Nov 13 15:27:14 rodney-P5Q-PRO wpa_supplicant[957]: CTRL-EVENT-CONNECTED - Connection to 40:61:86:9d:d5:83 completed (reauth) [id=0 id_str=]
Nov 13 15:27:14 rodney-P5Q-PRO NetworkManager[896]: <info> (wlan0): supplicant interface state: associated -> completed
Nov 13 15:32:14 rodney-P5Q-PRO kernel: [28956.596615] wlan0: deauthenticated from 40:61:86:9d:d5:83 (Reason: 3)
Nov 13 15:32:14 rodney-P5Q-PRO wpa_supplicant[957]: CTRL-EVENT-DISCONNECTED bssid=40:61:86:9d:d5:83 reason=3
Nov 13 15:32:14 rodney-P5Q-PRO NetworkManager[896]: <info> (wlan0): supplicant interface state: completed -> disconnected
Nov 13 15:32:14 rodney-P5Q-PRO NetworkManager[896]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 13 15:32:15 rodney-P5Q-PRO wpa_supplicant[957]: Trying to authenticate with 40:61:86:9d:d5:83 (SSID='wlan-ap' freq=2412 MHz)
Nov 13 15:32:15 rodney-P5Q-PRO NetworkManager[896]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 13 15:32:15 rodney-P5Q-PRO wpa_supplicant[957]: Trying to associate with 40:61:86:9d:d5:83 (SSID='wlan-ap' freq=2412 MHz)
Nov 13 15:32:15 rodney-P5Q-PRO kernel: [28957.504424] wlan0: authenticate with 40:61:86:9d:d5:83 (try 1)
Nov 13 15:32:15 rodney-P5Q-PRO kernel: [28957.505989] wlan0: authenticated
Nov 13 15:32:15 rodney-P5Q-PRO NetworkManager[896]: <info> (wlan0): supplicant interface state: authenticating -> associating
Nov 13 15:32:15 rodney-P5Q-PRO kernel: [28957.524074] wlan0: associate with 40:61:86:9d:d5:83 (try 1)
Nov 13 15:32:15 rodney-P5Q-PRO kernel: [28957.532229] wlan0: RX ReassocResp from 40:61:86:9d:d5:83 (capab=0x411 status=0 aid=1)
Nov 13 15:32:15 rodney-P5Q-PRO kernel: [28957.532233] wlan0: associated
Nov 13 15:32:15 rodney-P5Q-PRO wpa_supplicant[957]: Associated with 40:61:86:9d:d5:83
Nov 13 15:32:15 rodney-P5Q-PRO NetworkManager[896]: <info> (wlan0): supplicant interface state: associating -> associated
Nov 13 15:32:15 rodney-P5Q-PRO wpa_supplicant[957]: WPA: Key negotiation completed with 40:61:86:9d:d5:83 [PTK=TKIP GTK=TKIP]
Nov 13 15:32:15 rodney-P5Q-PRO wpa_supplicant[957]: CTRL-EVENT-CONNECTED - Connection to 40:61:86:9d:d5:83 completed (reauth) [id=0 id_str=]
Nov 13 15:32:15 rodney-P5Q-PRO NetworkManager[896]: <info> (wlan0): supplicant interface state: associated -> completed
Nov 13 15:36:49 rodney-P5Q-PRO NetworkManager[896]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
Nov 13 15:36:53 rodney-P5Q-PRO NetworkManager[896]: <info> (eth0): device state change: activated -> unavailable (reason 'carrier-changed') [100 20 40]
Nov 13 15:36:53 rodney-P5Q-PRO NetworkManager[896]: <info> (eth0): deactivating device (reason 'carrier-changed') [40]
Nov 13 15:36:54 rodney-P5Q-PRO NetworkManager[896]: <info> (eth0): canceled DHCP transaction, DHCP client pid 959
Nov 13 15:36:54 rodney-P5Q-PRO NetworkManager[896]: <info> Policy set 'wlan-ap' (wlan0) as default for IPv4 routing and DNS.
Nov 13 15:36:54 rodney-P5Q-PRO NetworkManager[896]: <info> Policy set 'wlan-ap' (wlan0) as default for IPv4 routing and DNS.



```

Rodney

---

### Post by chili555 on 2011-11-13
There are a couple of things you might try. First, if this is your router, you might set it to WPA2 only, instead of the current WPA and WPA2 mixed mode. You might also try a driver parameter:```
sudo gedit /etc/modprobe.d/ath9k.conf
```Add one line:```
options ath9k nohwcrypt=1
```Proofread, save and close gedit. Reboot and see if things are improved.

---

### Post by Rodney9 on 2011-11-13
> **chili555 said:**
> There are a couple of things you might try. First, if this is your router, you might set it to WPA2 only, instead of the current WPA and WPA2 mixed mode. You might also try a driver parameter:```
sudo gedit /etc/modprobe.d/ath9k.conf
```Add one line:```
options ath9k nohwcrypt=1
```Proofread, save and close gedit. Reboot and see if things are improved.

Thank You so much, it made a huge difference.


Rodney

---

