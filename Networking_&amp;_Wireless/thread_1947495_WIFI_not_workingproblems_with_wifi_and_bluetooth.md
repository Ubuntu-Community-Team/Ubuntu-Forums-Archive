---
title: "WIFI not working/problems with wifi and bluetooth"
date: 2012-03-26
forum: Networking &amp; Wireless
---

### Post by bobthe on 2012-03-26
i recently installed Wubi on my new hp dm4 beats edition. RAM = 8 gb, Core i7

my problems started when i tried to turn my bluetooth off but it would also turn my wifi off. after looking online, i ran the "rmmod iwlagn" and "modprobe iwlagn 11n_disable=0" commands

but that didn't do anything but made it worse as my wifi doesn't work at all. it can sense my wifi connection and tries to connect to it asking me the password multiple times but it still doesn't work.

can someone please help?!

---

### Post by bobthe on 2012-03-26
help!

---

### Post by wildmanne39 on 2012-03-26
Hi, did you make this > iwlagn 11n_disable=0 if not just reboot, did you make any other changes?

Then we will see if we can get bluetooth to work
Thanks

---

### Post by bobthe on 2012-03-26
i did do that. i've rebooted a couple times and wifi is still not working. note: i dont care about the bluetooth, i'm trying to turn that off and turn my wifi on. before when the wifi was working, whenever i turned off the bluetooth, it'd turn off the wifi as well. now the bluetooth is on but the wifi just won't work :/

---

### Post by wildmanne39 on 2012-03-26
Hi, please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by bobthe on 2012-03-26
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux ubuntu 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
09:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1030 [8086:008b] (rev 34)
	Subsystem: Intel Corporation Centrino Wireless-N 1030 BGN [8086:5315]
	Kernel driver in use: iwlagn
--
0b:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: Hewlett-Packard Company Device [103c:1793]
	Kernel driver in use: r8169
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
4: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
Module                  Size  Used by
parport_pc             36962  0 
ppdev                  17113  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
bnep                   18436  2 
rfcomm                 47946  8 
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_idt      70553  1 
joydev                 17693  0 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
arc4                   12529  2 
btusb                  18600  2 
bluetooth             166112  23 bnep,rfcomm,btusb
radeon               1015995  0 
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
psmouse                73882  0 
serio_raw              13166  0 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
iwlagn                314213  0 
snd_timer              29991  2 snd_pcm,snd_seq
i915                  566711  3 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
ttm                    76805  1 radeon
mac80211              310872  1 iwlagn
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rts_pstor             445246  0 
cfg80211              199587  2 iwlagn,mac80211
mei                    41480  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
drm_kms_helper         42558  2 radeon,i915
drm                   236330  6 radeon,ttm,i915,drm_kms_helper
i2c_algo_bit           13423  2 radeon,i915
wmi                    19256  1 hp_wmi
hp_accel               21880  0 
lis3lv02d              19888  1 hp_accel
video                  19412  1 i915
input_polldev          13896  1 lis3lv02d
ahci                   26002  1 
libahci                26861  1 ahci
xhci_hcd               78641  0 
r8169                  52788  0 

```

this is what i got

---

### Post by wildmanne39 on 2012-03-26
Hi, please post:
```
nm-tool
sudo iwlist scan
cat /var/lib/NetworkManager/NetworkManager.state
```
```
sudo cat /var/log/syslog | grep -e iwl -e firmware -e wpa -e wlan -e etork | tail -n55
```
Thanks

---

### Post by bobthe on 2012-03-26
this is for the first 3 commands : 
```

NetworkManager Tool

State: connecting

- Device: wlan0  [gr8punns] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlagn
  State:             connecting (configuring)
  Default:           no
  HW Address:        4C:EB:42:6A:BD:8C

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    SPECTRE:         Infra, C0:C1:C0:92:A0:39, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    Wireless77:      Infra, E0:46:9A:36:80:21, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA
    MCKELLSV-guest:  Infra, C0:C1:C0:10:A8:12, Freq 2462 MHz, Rate 54 Mb/s, Strength 39
    RadaFamily:      Infra, 00:25:9C:C2:9D:CB, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    2WIRE714:        Infra, 34:EF:44:49:52:A1, Freq 2447 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    NETGEAR84:       Infra, 20:4E:7F:B5:10:0A, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA2
    shyam24:         Infra, 68:7F:74:62:18:F1, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    gr8punns:        Infra, 00:1E:2A:0F:9E:0C, Freq 2437 MHz, Rate 54 Mb/s, Strength 87 WPA
    belkin.3f6:      Infra, 08:86:3B:2A:B3:F6, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    MCKELLSV:        Infra, C0:C1:C0:10:A8:10, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    Sanipini:        Infra, 00:18:39:53:81:AF, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WPA2
    bulldog:         Infra, 00:1D:6A:FE:AC:46, Freq 2437 MHz, Rate 54 Mb/s, Strength 65 WPA2
    MediaLink_6688:  Infra, C8:3A:35:3B:A0:18, Freq 2462 MHz, Rate 54 Mb/s, Strength 77 WPA


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        10:1F:74:6B:18:65

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


wlan0     Scan completed :
          Cell 01 - Address: 00:1E:2A:0F:9E:0C
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"gr8punns"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001163381c222
                    Extra: Last beacon: 428ms ago
                    IE: Unknown: 000867723870756E6E73
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0900037F0101001DFF7F
                    IE: Unknown: DD0C00037F0201011A0002A44000
                    IE: Unknown: DD1A00037F0301000000001E2A0F9E0C021E2A0F9E0C64002C011D08
          Cell 02 - Address: 00:1D:6A:FE:AC:46
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"bulldog"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000270086b3c18
                    Extra: Last beacon: 448ms ago
                    IE: Unknown: 000762756C6C646F67
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1013FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1606070500000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD1E00904C336E1013FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3406070500000000000000000000000000000000000000
          Cell 03 - Address: 00:18:39:53:81:AF
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"Sanipini"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000142f1bbcb0
                    Extra: Last beacon: 460ms ago
                    IE: Unknown: 000853616E6970696E69
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020014
          Cell 04 - Address: C8:3A:35:3B:A0:18
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"MediaLink_6688"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000167f4bb167
                    Extra: Last beacon: 132ms ago
                    IE: Unknown: 000E4D656469614C696E6B5F36363838
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160B070600000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010018127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706434E20010D10
                    IE: Unknown: DD1E00904C336E1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C340B070600000000000000000000000000000000000000
                    IE: Unknown: DD9E0050F204104A0001101044000101103B000103104700102880288028801880A880C83A353BA018102100174D656469616C696E6B2050726F64756374732C204C4C431023001B574952454C4553532D4E2031543152203135304D20524F55544552102400074150523135304E1042000831323334353637381054000800060050F20400011011000B4D574E2D4150523135304E100800020084103C000101
          Cell 05 - Address: C0:C1:C0:10:A8:10
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"MCKELLSV"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000b8aa337aa21
                    Extra: Last beacon: 352ms ago
                    IE: Unknown: 00084D434B454C4C5356
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001300000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7A0050F204104A00011010440001021041000100103B00010310470010445D440529A63AB18EAAB3E618FF620010210005436973636F1023000D4C696E6B7379732045333030301024000776312E302E30321042000234321054000800060050F20400011011000D4C696E6B737973204533303030100800020084
                    IE: Unknown: DD090010180201F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33FC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001300000000000000000000000000000000000000
          Cell 06 - Address: C0:C1:C0:10:A8:12
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:off
                    ESSID:"MCKELLSV-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000b8aa339bd33
                    Extra: Last beacon: 216ms ago
                    IE: Unknown: 000E4D434B454C4C53562D6775657374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001300000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180201F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33FC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001300000000000000000000000000000000000000
          Cell 07 - Address: C0:C1:C0:92:A0:39
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"SPECTRE"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000576bbfffe3
                    Extra: Last beacon: 548ms ago
                    IE: Unknown: 000753504543545245
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0102
                    IE: Unknown: 2F0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001700000000000000000000000000000000000000
                    IE: Unknown: DD690050F204104A0001101044000102103B00010310470010CA2A2FF5F5FF0C0A87CF76C834AE09D610210005436973636F102300054531353030102400063132333435361042000234321054000800060050F2040001101100054531353030100800020084103C000101
                    IE: Unknown: DD090010180203F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 08 - Address: 68:7F:74:62:18:F1
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"shyam24"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000004be54fd8
                    Extra: Last beacon: 448ms ago
                    IE: Unknown: 0007736879616D3234
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406080800000000000000000000000000000000000000
                    IE: Unknown: 3D1606080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD8F0050F204104A0001101044000102103B00010310470010687F746218FFFFFFF2000000000000001021001C4C696E6B7379732C2041204469766973696F6E206F6620436973636F102300075752543430304E102400075752543430304E1042000C4D554A30304B3131323932311054000800060050F2040001101100075752543430304E100800020086103C000103


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

```

second command:
```
Mar 26 18:58:59 ubuntu NetworkManager[1118]: <info> (wlan0): supplicant interface state: disconnected -> authenticating
Mar 26 18:58:59 ubuntu wpa_supplicant[1150]: Trying to associate with 00:1e:2a:0f:9e:0c (SSID='gr8punns' freq=2437 MHz)
Mar 26 18:58:59 ubuntu kernel: [ 1334.120956] wlan0: authenticate with 00:1e:2a:0f:9e:0c (try 1)
Mar 26 18:58:59 ubuntu kernel: [ 1334.124316] wlan0: authenticated
Mar 26 18:58:59 ubuntu kernel: [ 1334.124702] wlan0: associate with 00:1e:2a:0f:9e:0c (try 1)
Mar 26 18:58:59 ubuntu kernel: [ 1334.127388] wlan0: RX ReassocResp from 00:1e:2a:0f:9e:0c (capab=0x31 status=0 aid=4)
Mar 26 18:58:59 ubuntu kernel: [ 1334.127397] wlan0: associated
Mar 26 18:58:59 ubuntu wpa_supplicant[1150]: Associated with 00:1e:2a:0f:9e:0c
Mar 26 18:58:59 ubuntu NetworkManager[1118]: <info> (wlan0): supplicant interface state: authenticating -> associating
Mar 26 18:58:59 ubuntu NetworkManager[1118]: <info> (wlan0): supplicant interface state: associating -> associated
Mar 26 18:59:09 ubuntu wpa_supplicant[1150]: Authentication with 00:1e:2a:0f:9e:0c timed out.
Mar 26 18:59:09 ubuntu kernel: [ 1344.120106] wlan0: disassociating from 00:1e:2a:0f:9e:0c by local choice (reason=3)
Mar 26 18:59:09 ubuntu wpa_supplicant[1150]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=3
Mar 26 18:59:09 ubuntu wpa_supplicant[1150]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=3
Mar 26 18:59:10 ubuntu kernel: [ 1344.128121] wlan0: deauthenticating from 00:1e:2a:0f:9e:0c by local choice (reason=3)
Mar 26 18:59:09 ubuntu NetworkManager[1118]: <info> (wlan0): supplicant interface state: associated -> disconnected
Mar 26 18:59:10 ubuntu wpa_supplicant[1150]: Trying to authenticate with 00:1e:2a:0f:9e:0c (SSID='gr8punns' freq=2437 MHz)
Mar 26 18:59:10 ubuntu NetworkManager[1118]: <info> (wlan0): supplicant interface state: disconnected -> authenticating
Mar 26 18:59:10 ubuntu kernel: [ 1344.686400] wlan0: authenticate with 00:1e:2a:0f:9e:0c (try 1)
Mar 26 18:59:10 ubuntu kernel: [ 1344.689034] wlan0: authenticated
Mar 26 18:59:10 ubuntu wpa_supplicant[1150]: Trying to associate with 00:1e:2a:0f:9e:0c (SSID='gr8punns' freq=2437 MHz)
Mar 26 18:59:10 ubuntu kernel: [ 1344.689521] wlan0: associate with 00:1e:2a:0f:9e:0c (try 1)
Mar 26 18:59:10 ubuntu kernel: [ 1344.692554] wlan0: RX ReassocResp from 00:1e:2a:0f:9e:0c (capab=0x31 status=0 aid=4)
Mar 26 18:59:10 ubuntu kernel: [ 1344.692561] wlan0: associated
Mar 26 18:59:10 ubuntu NetworkManager[1118]: <info> (wlan0): supplicant interface state: authenticating -> associating
Mar 26 18:59:10 ubuntu wpa_supplicant[1150]: Associated with 00:1e:2a:0f:9e:0c
Mar 26 18:59:10 ubuntu NetworkManager[1118]: <info> (wlan0): supplicant interface state: associating -> associated
Mar 26 18:59:20 ubuntu wpa_supplicant[1150]: Authentication with 00:1e:2a:0f:9e:0c timed out.
Mar 26 18:59:20 ubuntu kernel: [ 1354.683371] wlan0: disassociating from 00:1e:2a:0f:9e:0c by local choice (reason=3)
Mar 26 18:59:20 ubuntu wpa_supplicant[1150]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=3
Mar 26 18:59:20 ubuntu wpa_supplicant[1150]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=3
Mar 26 18:59:20 ubuntu kernel: [ 1354.702661] wlan0: deauthenticating from 00:1e:2a:0f:9e:0c by local choice (reason=3)
Mar 26 18:59:20 ubuntu NetworkManager[1118]: <info> (wlan0): supplicant interface state: associated -> disconnected
Mar 26 18:59:21 ubuntu wpa_supplicant[1150]: Trying to authenticate with 00:1e:2a:0f:9e:0c (SSID='gr8punns' freq=2437 MHz)
Mar 26 18:59:21 ubuntu NetworkManager[1118]: <info> (wlan0): supplicant interface state: disconnected -> authenticating
Mar 26 18:59:21 ubuntu kernel: [ 1355.255414] wlan0: authenticate with 00:1e:2a:0f:9e:0c (try 1)
Mar 26 18:59:21 ubuntu wpa_supplicant[1150]: Trying to associate with 00:1e:2a:0f:9e:0c (SSID='gr8punns' freq=2437 MHz)
Mar 26 18:59:21 ubuntu kernel: [ 1355.267566] wlan0: authenticated
Mar 26 18:59:21 ubuntu kernel: [ 1355.268309] wlan0: associate with 00:1e:2a:0f:9e:0c (try 1)
Mar 26 18:59:21 ubuntu kernel: [ 1355.272817] wlan0: RX ReassocResp from 00:1e:2a:0f:9e:0c (capab=0x31 status=0 aid=4)
Mar 26 18:59:21 ubuntu kernel: [ 1355.272826] wlan0: associated
Mar 26 18:59:21 ubuntu wpa_supplicant[1150]: Associated with 00:1e:2a:0f:9e:0c
Mar 26 18:59:21 ubuntu NetworkManager[1118]: <info> (wlan0): supplicant interface state: authenticating -> associating
Mar 26 18:59:21 ubuntu NetworkManager[1118]: <info> (wlan0): supplicant interface state: associating -> associated
Mar 26 18:59:28 ubuntu NetworkManager[1118]: <warn> Activation (wlan0/wireless): association took too long.
Mar 26 18:59:28 ubuntu NetworkManager[1118]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Mar 26 18:59:28 ubuntu NetworkManager[1118]: <warn> Activation (wlan0/wireless): asking for new secrets
Mar 26 18:59:28 ubuntu kernel: [ 1362.166847] wlan0: deauthenticating from 00:1e:2a:0f:9e:0c by local choice (reason=3)
Mar 26 18:59:28 ubuntu wpa_supplicant[1150]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=3
Mar 26 18:59:28 ubuntu NetworkManager[1118]: <info> (wlan0): supplicant interface state: associated -> disconnected
Mar 26 18:59:33 ubuntu NetworkManager[1118]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Mar 26 18:59:33 ubuntu NetworkManager[1118]: <warn> Activation (wlan0) failed for access point (gr8punns)
Mar 26 18:59:33 ubuntu NetworkManager[1118]: <warn> Activation (wlan0) failed.
Mar 26 18:59:33 ubuntu NetworkManager[1118]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Mar 26 18:59:33 ubuntu NetworkManager[1118]: <info> (wlan0): deactivating device (reason 'none') [0]

```

edit: just found out that my ethernet connection isn't working either!

---

### Post by dandnsmith on 2012-03-27
That's quite likely because of the ethernet module/driver:
```
0b:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: Hewlett-Packard Company Device [103c:1793]
	Kernel driver in use: r8169
```
I would (and did) change to r8168 to get mine working on a couple of PCs with this problem (similar hardware).

There are threads on how to do this in this forum.

---

### Post by wildmanne39 on 2012-03-27
Hi, try this please:
```
sudo ifconfig wlan0 down
sudo rmmod -f iwlagn
sudo modprobe iwlagn 11n_disable=1
sudo ifconfig wlan0 up

```
if this works we will need to make it permanent so do not reboot.
Thanks

---

### Post by bobthe on 2012-03-31
Hi for some reason, the WiFi works now! I hadn't been on Ubuntu for some time and came back after few a few days and its working correctly!

---

### Post by wildmanne39 on 2012-03-31
Hi, I am glad it is working.

---

