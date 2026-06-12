---
title: "Latest updates have broken wireless"
date: 2012-04-06
forum: Networking &amp; Wireless
---

### Post by Alastair Rae on 2012-04-06
My Sony Vaio is on 11.10 and it used to connect automatically to my local wireless modem. I just installed all the recent updates. Now after a reboot it does not automatically connect. I have to go into Connect to Hidden Wireless Network and select my network. Then it sits "connecting" for a minute and then prompts "Authentication required by wireless network". If I click on Show Key the remembered wireless password is correct. It tries again for another minute and prompts again. Help!

---

### Post by wildmanne39 on 2012-04-06
Hi, please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod

```
Thanks

---

### Post by Alastair Rae on 2012-04-07
Here's the extra info:
```

+ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
+ uname -a
Linux merula-laptop 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 20:45:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
+ lspci -nnk
+ grep -iA2 net
07:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: Foxconn International, Inc. Device [105b:e037]
	Kernel driver in use: ath9k
--
13:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: Sony Corporation Device [104d:908b]
	Kernel driver in use: r8169
+ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 064e:a302 Suyin Corp. 
Bus 001 Device 004: ID 0489:e027 Foxconn / Hon Hai 
Bus 002 Device 003: ID 413c:3200 Dell Computer Corp. Mouse
Bus 002 Device 004: ID 0781:5151 SanDisk Corp. Cruzer Micro Flash Drive
+ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
+ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: sony-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: sony-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
+ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61475  1 vfat
usb_storage            57901  1 
uas                    18027  0 
parport_pc             36962  0 
ppdev                  17113  0 
bnep                   18436  2 
rfcomm                 47946  0 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_conexant    62197  1 
joydev                 17693  0 
binfmt_misc            17540  1 
snd_hda_intel          33390  2 
snd_hda_codec         104931  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
usbhid                 47198  0 
hid                    95463  1 usbhid
arc4                   12529  2 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
btusb                  18600  1 
snd_seq_midi_event     14899  1 snd_seq_midi
bluetooth             166112  13 bnep,rfcomm,btusb
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
ath9k                 127538  0 
snd_timer              29991  2 snd_pcm,snd_seq
mac80211              462046  1 ath9k
sony_laptop            45393  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
ath9k_common           13839  1 ath9k
ath9k_hw              312914  2 ath9k,ath9k_common
ath                    24067  2 ath9k,ath9k_hw
cfg80211              199630  3 ath9k,mac80211,ath
rts_pstor             445246  0 
psmouse                73882  0 
serio_raw              13166  0 
i915                  571251  3 
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         42558  1 i915
mei                    41480  0 
drm                   236290  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
soundcore              12680  1 snd
video                  19412  1 i915
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  52788  0 
ahci                   26002  2 
libahci                26861  1 ahci

```

---

### Post by wildmanne39 on 2012-04-07
Hi, please post the output from the following commands while you can not connect:
```
nm-tool
sudo iwlist scan
cat /var/lib/NetworkManager/NetworkManager.state
```
```
sudo cat /var/log/syslog | grep -e ath -e firmware -e wpa -e wlan -e etork | tail -n55
```
Thanks

---

### Post by Alastair Rae on 2012-04-07
When trying to connect the output is as below. There are a whole bunch of other networks in range - my own local wifi is called "Merula".
```
+ nm-tool

NetworkManager Tool

State: connecting

- Device: wlan0  [Merula] ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connecting (configuring)
  Default:           no
  HW Address:        90:00:4E:C4:04:B3

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Merula:          Infra, 00:26:44:09:62:65, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WEP
    85Parkhurst:     Infra, 00:26:F2:62:52:4C, Freq 2437 MHz, Rate 54 Mb/s, Strength 9 WPA
    BTFON:           Infra, 12:FE:F4:41:02:20, Freq 2462 MHz, Rate 54 Mb/s, Strength 34
    CJPLAPTOP_Network: Infra, 74:EA:3A:BA:89:9C, Freq 2427 MHz, Rate 54 Mb/s, Strength 25 WPA2
    auwlan2:         Infra, 00:23:68:05:AE:E5, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA
    VirginBroadband_flat23: Infra, 00:22:3F:1F:05:A2, Freq 2447 MHz, Rate 54 Mb/s, Strength 12 WPA
    Dlink:           Infra, 1C:BD:B9:AD:A5:7E, Freq 2432 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    BTHub3-W2J9:     Infra, 00:FE:F4:22:22:20, Freq 2462 MHz, Rate 54 Mb/s, Strength 10 WPA WPA2
    BTFON:           Infra, 12:FE:F4:22:AF:A8, Freq 2412 MHz, Rate 48 Mb/s, Strength 42
    BTHub3-CMXQ:     Infra, 00:FE:F4:22:AF:A8, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    iPhone:          Infra, EE:85:2F:33:52:40, Freq 2417 MHz, Rate 54 Mb/s, Strength 17 WPA2
    BTBusinessHub-498: Infra, 64:0F:29:0E:9E:C9, Freq 2447 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    StreetNet:       Infra, 00:0D:67:00:63:9D, Freq 2412 MHz, Rate 54 Mb/s, Strength 14
    virginmedia1423539: Infra, C4:3D:C7:43:5A:98, Freq 2462 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2
    virginmedia2210403: Infra, 00:1E:2A:7E:03:1A, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    TALKTALK-9663E1: Infra, 34:08:04:96:63:E1, Freq 2412 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    BTHub3-CMXQ:     Infra, 00:FE:F4:22:AF:A8, Freq 2412 MHz, Rate 48 Mb/s, Strength 30 WEP
    BTHub3-3T4K:     Infra, 00:FE:F4:79:87:78, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    BTOpenzone-H:    Infra, 02:FE:F4:41:02:20, Freq 2462 MHz, Rate 54 Mb/s, Strength 32
    BTOpenzone-H:    Infra, 02:FE:F4:22:AF:A8, Freq 2412 MHz, Rate 54 Mb/s, Strength 34
    O2wireless197937:Infra, 00:26:44:1C:E9:EF, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WEP
    SKY62001:        Infra, 00:1E:74:D3:F2:32, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA
    SKY57220:        Infra, 34:08:04:9B:A9:21, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    PlusnetWireless293C7C: Infra, 58:98:35:29:3C:7C, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    virginmedia6864742: Infra, A0:21:B7:CB:A6:75, Freq 2432 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    virginmedia6215297: Infra, A0:21:B7:EA:9A:1D, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    belkin54g:       Infra, 00:11:50:FB:9B:98, Freq 2412 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2
    virginmedia6526056: Infra, 00:1E:2A:7F:68:B4, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    NecroSS:         Infra, 00:24:B2:C5:6F:72, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA
    virginmedia1784436: Infra, A0:21:B7:E2:C3:71, Freq 2432 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    GoldenVirginia:  Infra, 58:6D:8F:36:9A:68, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    H402LEM:         Infra, 00:26:44:F8:40:61, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    DSL-2640R:       Infra, 00:24:01:0E:29:27, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    TALKTALK-BAB130: Infra, 84:C9:B2:BA:B1:30, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    BTHub3-R2HZ:     Infra, 00:FE:F4:41:02:20, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        78:84:3C:E3:C9:17

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


+ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: A0:21:B7:CB:A6:75
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"virginmedia6864742"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002c5c7302b0
                    Extra: Last beacon: 664ms ago
                    IE: Unknown: 001276697267696E6D6564696136383634373432
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030105
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D16050D0000000000000000000000000000000000000000
                    IE: Unknown: DD710050F204104A0001101044000102103B000103104700104D73C5C27E6B5243D6440AAB1719670B102100074E657467656172102300074E6574676561721024000631323334353610420007303030303030311054000800060050F2040001101100094E6574676561724150100800020088
                    IE: Unknown: DD090010180200F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34050D0000000000000000000000000000000000000000
          Cell 02 - Address: 12:FE:F4:41:02:20
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:off
                    ESSID:"BTFON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001a4b2e6d80
                    Extra: Last beacon: 220ms ago
                    IE: Unknown: 00054254464F4E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001300000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101870003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33AC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001300000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 03 - Address: 02:FE:F4:41:02:20
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:off
                    ESSID:"BTOpenzone-H"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001a4b2ed180
                    Extra: Last beacon: 192ms ago
                    IE: Unknown: 000C42544F70656E7A6F6E652D48
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001300000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101870003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33AC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001300000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 04 - Address: 00:FE:F4:41:02:20
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"BTHub3-R2HZ"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001a4b2d41b1
                    Extra: Last beacon: 244ms ago
                    IE: Unknown: 000B4254487562332D5232485A
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001300000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101870003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33AC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001300000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 05 - Address: 00:26:44:F8:40:61
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"H402LEM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002c597662d9
                    Extra: Last beacon: 616ms ago
                    IE: Unknown: 0007483430324C454D
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A0C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001100000000000000000000000000000000000000
                    IE: Unknown: DD09001018020000050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101080003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C330C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001100000000000000000000000000000000000000
          Cell 06 - Address: 02:FE:F4:22:AF:A8
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:"BTOpenzone-H"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000007b29aa570
                    Extra: Last beacon: 5448ms ago
                    IE: Unknown: 000C42544F70656E7A6F6E652D48
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001300000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33AC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001300000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 07 - Address: 58:6D:8F:36:9A:68
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"GoldenVirginia"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002c5bbb32fd
                    Extra: Last beacon: 4932ms ago
                    IE: Unknown: 000E476F6C64656E56697267696E6961
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081100000000000000000000000000000000000000
                    IE: Unknown: DD860050F204104A0001101044000102103B00010310470010255B50C6133B48672FCBBB13B5131E55102100074C696E6B7379731023000D4C696E6B7379732045333230301024000776312E302E30311042000234321054000800060050F20400011011000D4C696E6B737973204533323030100800022008103C0001031049000600372A000120
                    IE: Unknown: DD090010180200F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 08 - Address: A0:21:B7:E2:C3:71
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"virginmedia1784436"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002bb394518a
                    Extra: Last beacon: 696ms ago
                    IE: Unknown: 001276697267696E6D6564696131373834343336
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030105
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D16050D1600000000000000000000000000000000000000
                    IE: Unknown: DD710050F204104A0001101044000102103B000103104700104D73C5C27E6B5243D6440AAB1719670B102100074E657467656172102300074E6574676561721024000631323334353610420007303030303030311054000800060050F2040001101100094E6574676561724150100800020088
                    IE: Unknown: DD090010180201F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34050D1600000000000000000000000000000000000000
          Cell 09 - Address: 00:FE:F4:79:87:78
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"BTHub3-3T4K"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002bad3240f3
                    Extra: Last beacon: 872ms ago
                    IE: Unknown: 000B4254487562332D3354344B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101870003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33AC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001100000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 10 - Address: C4:3D:C7:43:5A:98
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"virginmedia1423539"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002bb3b9d187
                    Extra: Last beacon: 4944ms ago
                    IE: Unknown: 001276697267696E6D6564696131343233353339
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: DD6F0050F204104A0001101044000102103B000103104700104D73C5C27E6B5243D6440AAB1719670B102100074E657467656172102300074E6574676561721024000631323334353610420007303030303030311054000800060050F20400011011000743473331303144100800020088
                    IE: Unknown: DD090010180201F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B081500000000000000000000000000000000000000
          Cell 11 - Address: 00:24:01:0E:29:27
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"DSL-2640R"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002bb3b88593
                    Extra: Last beacon: 892ms ago
                    IE: Unknown: 000944534C2D3236343052
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 12 - Address: 00:24:B2:C5:6F:72
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"NecroSS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002bb3548751
                    Extra: Last beacon: 604ms ago
                    IE: Unknown: 00074E6563726F5353
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 13 - Address: 00:1E:2A:7F:68:B4
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"virginmedia6526056"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002bb2fe519e
                    Extra: Last beacon: 11424ms ago
                    IE: Unknown: 001276697267696E6D6564696136353236303536
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1601051700000000000000000000000000000000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180202F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401051700000000000000000000000000000000000000
          Cell 14 - Address: 00:23:68:05:AE:E5
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"auwlan2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002baf7d71dc
                    Extra: Last beacon: 11436ms ago
                    IE: Unknown: 00076175776C616E32
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 0504020A0000
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 2A0106
                    IE: Unknown: 32043048606C
                    IE: Unknown: AD0F00A0F8000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: 58:98:35:29:3C:7C
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"PlusnetWireless293C7C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002bab69b2e5
                    Extra: Last beacon: 5200ms ago
                    IE: Unknown: 0015506C75736E6574576972656C657373323933433743
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A0C0017FF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000100000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: DD1E00904C330C0017FF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406000100000000000000000000000000000000000000
          Cell 16 - Address: 00:1E:2A:7E:03:1A
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"virginmedia2210403"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002c5bc7b186
                    Extra: Last beacon: 11416ms ago
                    IE: Unknown: 001276697267696E6D6564696132323130343033
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D16010D1100000000000000000000000000000000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180200F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34010D1100000000000000000000000000000000000000
          Cell 17 - Address: 84:C9:B2:BA:B1:30
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"TALKTALK-BAB130"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002c5b63b169
                    Extra: Last beacon: 832ms ago
                    IE: Unknown: 000F54414C4B54414C4B2D424142313330
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601050100000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000009127A
                    IE: Unknown: DD1E00904C33EE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3401050100000000000000000000000000000000000000
                    IE: Unknown: DD07000C4307000000
          Cell 18 - Address: 12:FE:F4:22:AF:A8
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:off
                    ESSID:"BTFON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000007b2e09c9f
                    Extra: Last beacon: 860ms ago
                    IE: Unknown: 00054254464F4E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001300000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33AC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001300000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 19 - Address: 34:08:04:9B:A9:21
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"SKY57220"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002c5bf721b6
                    Extra: Last beacon: 604ms ago
                    IE: Unknown: 0008534B593537323230
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 20 - Address: A0:21:B7:EA:9A:1D
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"virginmedia6215297"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000115d0ff770
                    Extra: Last beacon: 628ms ago
                    IE: Unknown: 001276697267696E6D6564696136323135323937
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081100000000000000000000000000000000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180200F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406081100000000000000000000000000000000000000
          Cell 21 - Address: 64:0F:29:0E:9E:CC
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:off
                    ESSID:"BTOpenzone"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000024b945181
                    Extra: Last beacon: 524ms ago
                    IE: Unknown: 000A42544F70656E7A6F6E65
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030108
                    IE: Unknown: 050400030000
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101850003A4000027A4000042435E0062322F00

+ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true
+ echo

+ sudo cat /var/log/syslog
+ grep -e ath -e firmware -e wpa -e wlan -e etork
+ tail -n55
Apr  7 20:29:49 merula-laptop dhclient: Sending on   LPF/wlan0/90:00:4e:c4:04:b3
Apr  7 20:29:49 merula-laptop dhclient: DHCPREQUEST of 10.215.167.116 on wlan0 to 255.255.255.255 port 67
Apr  7 20:29:49 merula-laptop NetworkManager[833]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Apr  7 20:29:49 merula-laptop NetworkManager[833]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Apr  7 20:29:49 merula-laptop NetworkManager[833]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Apr  7 20:29:49 merula-laptop NetworkManager[833]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Apr  7 20:29:49 merula-laptop avahi-daemon[835]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.215.167.116.
Apr  7 20:29:49 merula-laptop avahi-daemon[835]: New relevant interface wlan0.IPv4 for mDNS.
Apr  7 20:29:49 merula-laptop avahi-daemon[835]: Registering new address record for 10.215.167.116 on wlan0.IPv4.
Apr  7 20:29:50 merula-laptop NetworkManager[833]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Apr  7 20:29:50 merula-laptop NetworkManager[833]: <info> Policy set 'BTFON' (wlan0) as default for IPv4 routing and DNS.
Apr  7 20:29:50 merula-laptop NetworkManager[833]: <info> Activation (wlan0) successful, device activated.
Apr  7 20:29:50 merula-laptop NetworkManager[833]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Apr  7 20:29:50 merula-laptop NetworkManager[833]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Apr  7 20:29:51 merula-laptop avahi-daemon[835]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::9200:4eff:fec4:4b3.
Apr  7 20:29:51 merula-laptop avahi-daemon[835]: New relevant interface wlan0.IPv6 for mDNS.
Apr  7 20:29:51 merula-laptop avahi-daemon[835]: Registering new address record for fe80::9200:4eff:fec4:4b3 on wlan0.*.
Apr  7 20:30:00 merula-laptop kernel: [  623.572023] wlan0: no IPv6 routers present
Apr  7 20:30:00 merula-laptop NetworkManager[833]: <info> (wlan0): disconnecting for new activation request.
Apr  7 20:30:00 merula-laptop NetworkManager[833]: <info> (wlan0): device state change: activated -> disconnected (reason 'none') [100 30 0]
Apr  7 20:30:00 merula-laptop NetworkManager[833]: <info> (wlan0): deactivating device (reason 'none') [0]
Apr  7 20:30:01 merula-laptop NetworkManager[833]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1846
Apr  7 20:30:01 merula-laptop avahi-daemon[835]: Withdrawing address record for 10.215.167.116 on wlan0.
Apr  7 20:30:01 merula-laptop avahi-daemon[835]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 10.215.167.116.
Apr  7 20:30:01 merula-laptop kernel: [  624.275210] wlan0: deauthenticating from 12:fe:f4:41:02:20 by local choice (reason=3)
Apr  7 20:30:01 merula-laptop wpa_supplicant[843]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=3
Apr  7 20:30:01 merula-laptop avahi-daemon[835]: Interface wlan0.IPv4 no longer relevant for mDNS.
Apr  7 20:30:01 merula-laptop NetworkManager[833]: <info> Activation (wlan0) starting connection 'Merula'
Apr  7 20:30:01 merula-laptop NetworkManager[833]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Apr  7 20:30:01 merula-laptop NetworkManager[833]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr  7 20:30:01 merula-laptop NetworkManager[833]: <info> (wlan0): supplicant interface state: completed -> disconnected
Apr  7 20:30:01 merula-laptop NetworkManager[833]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr  7 20:30:01 merula-laptop NetworkManager[833]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr  7 20:30:01 merula-laptop NetworkManager[833]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr  7 20:30:01 merula-laptop NetworkManager[833]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr  7 20:30:01 merula-laptop NetworkManager[833]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr  7 20:30:01 merula-laptop NetworkManager[833]: <info> Activation (wlan0/wireless): access point 'Merula' has security, but secrets are required.
Apr  7 20:30:01 merula-laptop NetworkManager[833]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Apr  7 20:30:01 merula-laptop NetworkManager[833]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr  7 20:30:01 merula-laptop NetworkManager[833]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr  7 20:30:01 merula-laptop NetworkManager[833]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr  7 20:30:01 merula-laptop NetworkManager[833]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Apr  7 20:30:01 merula-laptop NetworkManager[833]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr  7 20:30:01 merula-laptop NetworkManager[833]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr  7 20:30:01 merula-laptop NetworkManager[833]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr  7 20:30:01 merula-laptop NetworkManager[833]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr  7 20:30:01 merula-laptop NetworkManager[833]: <info> Activation (wlan0/wireless): connection 'Merula' has security, and secrets exist.  No new secrets needed.
Apr  7 20:30:01 merula-laptop NetworkManager[833]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr  7 20:30:01 merula-laptop NetworkManager[833]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Apr  7 20:30:02 merula-laptop wpa_supplicant[843]: Trying to authenticate with 00:26:44:09:62:65 (SSID='Merula' freq=2437 MHz)
Apr  7 20:30:02 merula-laptop NetworkManager[833]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Apr  7 20:30:02 merula-laptop kernel: [  625.273927] wlan0: direct probe to 00:26:44:09:62:65 (try 1/3)
Apr  7 20:30:02 merula-laptop kernel: [  625.471471] wlan0: direct probe to 00:26:44:09:62:65 (try 2/3)
Apr  7 20:30:02 merula-laptop kernel: [  625.671383] wlan0: direct probe to 00:26:44:09:62:65 (try 3/3)
Apr  7 20:30:02 merula-laptop kernel: [  625.871327] wlan0: direct probe to 00:26:44:09:62:65 timed out

```

---

### Post by wildmanne39 on 2012-04-07
Hi, your wireless signal is very weak it is trying to connect to another network first.

I recommend unhiding your network it is very difficult for ubuntu to connect to a hidden network and it is just as easy for a hacker to break into a hidden network as it is one that broadcasts.

Your signal strength is very weak to weak for you to connect.

Also it is best if you can set the encryption in your router to just wpa2.

Please do:
```
gksudo gedit /etc/modprobe.d/ath9k.conf
```

Add a single line:

```
options ath9k nohwcrypt=1
```

Proofread carefully, save and close gedit. Reboot.
Thanks

---

### Post by Alastair Rae on 2012-04-08
I tried that. Even if I have the laptop right next to the modem, it still won't connect so I don't think signal strength is the problem. 

Something in the recent updates has broken wifi. How can I back out the updates that made it stop working? Or is there a more stable release than 11.10 I could try? Maybe I should go back to 10.x because that used to be very reliable.

---

### Post by kevdog on 2012-04-08
I'm speculating when you mean the "most recent upgrades", I guessing your kernel was upgraded.  Why don't you try booting back into the previous kernel to see if this changes your situation.  You can select the option for this from the grub2 menu at boot.

---

### Post by wildmanne39 on 2012-04-08
Hi, post the contents of:
```
gksudo gedit /etc/modprobe.d/ath9k.conf
```

Did you change your encryption to wpa2 in the router?

When you ran sudo iwlist scan your router was not even found.

In the other information it was but very weak.

Have you reset your router?

You can try another channel with less people on it.

You can install wicd then remove network manager in that order.
Thanks

---

### Post by bonesdds on 2012-04-25
Bump.  I am also suffering from the update related broken wireless.  I do not have a weak signal or a hidden network.  I can see the WPA2 network, but not access it.  If I boot the live CD I can connect, but booting the previous kernel, reloading drivers and all other efforts fail. I was able to get it to connect once by hibernating, as suggested in another thread.  I noticed that Libpam was updated when things stopped working, so it may be related.  Also, modem manager freezes the system on shutdown when wireless is enabled.  Any help is appreciated.

---

