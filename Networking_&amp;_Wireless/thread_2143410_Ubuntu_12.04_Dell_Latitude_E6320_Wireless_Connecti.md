---
title: "Ubuntu 12.04 Dell Latitude E6320 Wireless Connectivity Problem"
date: 2013-05-09
forum: Networking &amp; Wireless
---

### Post by pcman312 on 2013-05-09
I recently did an update on my E6320 running Ubuntu 12.04 and after a reboot, the wireless no longer connects. It was connecting prior to the update via wireless, so something in the update must have screwed up the network connection.

Behavior:
Wireless attempts to connect to wifi
Wireless connection eventually times out and stops trying to connect
No password is requested because the saved connection has the password - it never re-requests it

Connection Info:
IPv4 settings:
Automatic (DHCP) addresses only
DNS Servers: 8.8.8.8, 8.8.4.4
Require IPv4 addressing for this connection to complete - checked

IPv6 settings:
Ignore

NOTE: I did these two updates because my wireless was not working when I first got the laptop and this fixed the issue at the time. I have tried turning these both back to Automatic without any luck.

Per other posts from **Wild Man**, I used the wireless_script that he provided to generate this info as well:
```

*************** info trace ****************



**** uname -a ****


Linux Ganymede 3.2.0-41-generic #66-Ubuntu SMP Thu Apr 25 03:27:11 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"


**** lspci ****


00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
	Subsystem: Dell Device [1028:0492]
	Kernel driver in use: e1000e
--
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
	Subsystem: Dell Inspiron M5010 / XPS 8300 [1028:0010]
	Kernel driver in use: wl


**** lsusb ****


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 413c:8187 Dell Computer Corp. DW375 Bluetooth Module
Bus 002 Device 003: ID 05dc:a205 Lexar Media, Inc. 
Bus 002 Device 004: ID 0a5c:5801 Broadcom Corp. BCM5880 Secure Applications Processor with fingerprint swipe sensor


**** iwconfig ****


eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


**** rfkill ****


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
4: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no


**** lsmod ****


Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
michael_mic            12612  0 
arc4                   12529  0 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
joydev                 17693  0 
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
dell_laptop            18119  0 
dcdbas                 14490  1 dell_laptop
lib80211_crypt_tkip    17390  0 
snd_hda_intel          33719  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
psmouse                97485  0 
btusb                  18332  2 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13211  0 
wl                   3074895  0 
i915                  477763  3 
snd                    79041  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         46978  1 i915
drm                   241971  4 i915,drm_kms_helper
wmi                    19256  1 dell_wmi
i2c_algo_bit           13423  1 i915
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41616  0 
video                  19651  1 i915
bnep                   18281  2 
cfg80211              205774  1 wl
mac_hid                13253  0 
rfcomm                 47604  12 
bluetooth             180153  23 btusb,bnep,rfcomm
lib80211               14381  2 lib80211_crypt_tkip,wl
parport_pc             32866  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
e1000e                156873  0 
usb_storage            49198  1 


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    HOME-1082:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 65 WPA WPA2
    Babs:            Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    HOME-6988:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    HOME-9122:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    PorterWiFi:      Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    omega:           Infra, <MAC address removed>, Freq 2422 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    DENTB_BRIDGE:    Infra, <MAC address removed>, Freq 2432 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    sailfish:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 12 WPA WPA2
    Zogg:            Infra, <MAC address removed>, Freq 2432 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    Renaissance_Guest: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24
    TownePlace_GUEST:Infra, <MAC address removed>, Freq 2432 MHz, Rate 54 Mb/s, Strength 15
    Renaissance_Guest: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 14
    Renaissance_Guest: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 12
    Renaissance_Guest: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22
    amy sembower:    Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 9 WPA2
    Renaissance_Guest: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 14
    Renaissance_Guest: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19
    Renaissance_Guest: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22
    Renaissance_Guest: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 15
    Renaissance_Guest: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20
    Renaissance_Guest: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 14
    Renaissance_Guest: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 14
    Renaissance_Guest: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20
    Dorothy  Mathis's Network: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 10 WPA2
    PuraVida:        Infra, <MAC address removed>, Freq 2422 MHz, Rate 54 Mb/s, Strength 9 WPA WPA2
    Cerberus:        Infra, <MAC address removed>, Freq 2432 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    REDMONDPIE 2.4:  Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA2
    ProjectMayhem:   Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 12 WPA WPA2


- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.197
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1




**** NetworkManager.state ****



[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


**** NetworkManager.conf ****



[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC address removed>,

[ifupdown]
managed=false


**** NetworkManager.conf-10.04 ****




**** interfaces ****


auto lo
iface lo inet loopback



**** iwlist ****


eth1      Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:on
                    ESSID:"Cerberus"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 00084365726265727573
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030108
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160800180000000F000000000000000000000000000000
                    IE: Unknown: DD1E00904C336C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340800000000000F000000000000000000000000000000
                    IE: Unknown: DD7F0050F204104A0001101044000102103B000103104700104CF22DCB397D3D5087C145A82DE67F8D1021000E442D4C696E6B2053797374656D73102300074449522D363535102400024134104200046E6F6E651054000800060050F204000110110017587472656D65204E204749474142495420526F75746572100800020084
          Cell 02 - Address: <MAC address removed>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"omega"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 00056F6D656761
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030103
                    IE: Unknown: 050401020000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 3204B048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3403051B00000000000000000000000000000000000000
                    IE: Unknown: 3D1603051B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD270050F204104A00011010440001021047001000000000000010000000E091F5B00E6E103C000103
          Cell 03 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"HOME-1082"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 0009484F4D452D31303832
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 070C55532001010F0209110B010F
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD270050F204104A0001101044000102104700102880288028801880A880001DD6AA1080103C000101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0106
                    IE: Unknown: 2D1A0C0016FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1601000500000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010049127A
                    IE: Unknown: DD07000C4307000000
          Cell 04 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"Babs"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 000442616273
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010010
                    IE: Unknown: DD310050F204104A0001101044000102104700102880288028801880A880B89BC95CB698103C0001011049000600372A000120
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEE1117FFFFFF0001000000000000000000000000030000000000
                    IE: Unknown: 3D1601000600000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0502001D127A
                    IE: Unknown: DD07000C4300000000
          Cell 05 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"HOME-9122"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 0009484F4D452D39313232
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 070C55532001010F0209110B010F
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD270050F204104A0001101044000102104700102880288028801880A880001DD6A09120103C000101
                    IE: Unknown: 0504000100D2
                    IE: Unknown: 2A0106
                    IE: Unknown: 2D1A0C0016FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1601000700000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010038127A
                    IE: Unknown: DD07000C4307000000
          Cell 06 - Address: <MAC address removed>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"Zogg"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 00045A6F6767
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030105
                    IE: Unknown: 050401020000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 3204B048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34050D0A00000000000000000000000000000000000000
                    IE: Unknown: 3D16050D0A00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD270050F204104A00011010440001021047001000000000000010000000A021B7B39C66103C000103
          Cell 07 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"PorterWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 000A506F7274657257694669
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
                    IE: Unknown: 3D1606081500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180204F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 08 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEE1117FFFFFF0001000000000000000000000000030000000000
                    IE: Unknown: 3D160B070600000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010018127A
                    IE: Unknown: DD07000C4300000000
          Cell 09 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEE1117FFFFFF0001000000000000000000000000030000000000
                    IE: Unknown: 3D160B070600000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010018127A
                    IE: Unknown: DD07000C4300000000
          Cell 10 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"HOME-6988"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 0009484F4D452D36393838
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010018
                    IE: Unknown: DD310050F204104A0001101044000102104700102880288028801880A88078CD8EE96988103C0001011049000600372A000120
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEE1117FFFFFF0001000000000000000000000000030000000000
                    IE: Unknown: 3D160B070600000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010018127A
                    IE: Unknown: DD07000C4300000000
          Cell 11 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEE1117FFFFFF0001000000000000000000000000030000000000
                    IE: Unknown: 3D160B070600000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010018127A
                    IE: Unknown: DD07000C4300000000
          Cell 12 - Address: <MAC address removed>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"DENTB_BRIDGE"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 11260ms ago
                    IE: Unknown: 000C44454E54425F425249444745
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030105
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD180050F2020101890007A4000023A4000042435E0062322F00
                    IE: Unknown: DD1E00904C338C011BFFFF000000000000000000001000000000000000000000
                    IE: Unknown: 2D1A8C011BFFFF000000000000000000001000000000000000000000
                    IE: Unknown: DD1A00904C3405000000000000000000000000000000000000000000
                    IE: Unknown: 3D1605000000000000000000000000000000000000000000
                    IE: Unknown: 7F0400000000
                    IE: Unknown: DD080013920100018500
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"sailfish"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 00087361696C66697368
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
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081100000000000000000000000000000000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180200F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 14 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"Dorothy  Mathis's Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 0019446F726F74687920204D61746869732773204E6574776F726B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050401030000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A2C4017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601000400000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000393016B0320
                    IE: Unknown: DD070017F203020180
                    IE: Unknown: DD0E0017F2070001010668A86D5B39EB
          Cell 15 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:off
                    ESSID:"Renaissance_Guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 001152656E61697373616E63655F4775657374
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD180050F20201018D0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD080013920100018500
          Cell 16 - Address: <MAC address removed>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:off
                    ESSID:"TownePlace_GUEST"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 0010546F776E65506C6163655F4755455354
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030105
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD180050F2020101890007A4000023A4000042435E0062322F00
                    IE: Unknown: DD1E00904C338C011BFFFF000000000000000000001000000000000000000000
                    IE: Unknown: 2D1A8C011BFFFF000000000000000000001000000000000000000000
                    IE: Unknown: DD1A00904C3405000000000000000000000000000000000000000000
                    IE: Unknown: 3D1605000000000000000000000000000000000000000000
                    IE: Unknown: 7F0400000000
                    IE: Unknown: DD080013920100018500
          Cell 17 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=16/70  Signal level=-94 dBm  
                    Encryption key:off
                    ESSID:"Renaissance_Guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 001152656E61697373616E63655F4775657374
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 050400010100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD180050F20201018D0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD080013920100018500
          Cell 18 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=16/70  Signal level=-94 dBm  
                    Encryption key:off
                    ESSID:"Renaissance_Guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 001152656E61697373616E63655F4775657374
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 05040001003C
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD180050F20201018D0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD080013920100018500
          Cell 19 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:off
                    ESSID:"Renaissance_Guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 001152656E61697373616E63655F4775657374
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010002
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD180050F20201018D0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD080013920100018500
          Cell 20 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:off
                    ESSID:"Renaissance_Guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 001152656E61697373616E63655F4775657374
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD180050F20201018D0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD080013920100018500



**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search hsd1.co.comcast.net


**** blacklist.conf ****


# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac


**** dmesg ****


[    2.241375] ACPI Error: [EABF] Namespace lookup failure, AE_ALREADY_EXISTS (20110623/dswload2-316)
[    5.398161] wmi: Mapper loaded
[    5.414863] wl: module license 'MIXED/Proprietary' taints kernel.
[    5.471548] wl 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    5.471562] wl 0000:02:00.0: setting latency timer to 64
[    5.661395] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[    5.738151] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 6.20.155.1 (r326264)
[   18.803829] eth1: no IPv6 routers present
[   68.814270] eth1: no IPv6 routers present
[  116.943858] eth1: no IPv6 routers present
[  167.700772] eth1: no IPv6 routers present
[  512.897235] eth1: no IPv6 routers present
[  562.927432] eth1: no IPv6 routers present
[  572.607226] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[  572.607237] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[  572.607253] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[  572.607259] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[  572.607272] ERROR @wl_dev_intvar_get : error (-1)
[  572.607277] ERROR @wl_cfg80211_get_tx_power : error (-1)
[  611.112984] eth1: no IPv6 routers present
[  624.632446] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[  624.632458] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[  624.632475] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[  624.632481] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[  624.632494] ERROR @wl_dev_intvar_get : error (-1)
[  624.632499] ERROR @wl_cfg80211_get_tx_power : error (-1)
[  641.306809] eth1: no IPv6 routers present
[  690.378690] eth1: no IPv6 routers present
[  876.647591] eth1: no IPv6 routers present
[ 1222.396207] eth1: no IPv6 routers present
[ 1253.870084] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[ 1253.870095] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[ 1253.870111] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[ 1253.870117] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[ 1253.870130] ERROR @wl_dev_intvar_get : error (-1)
[ 1253.870136] ERROR @wl_cfg80211_get_tx_power : error (-1)
[ 1268.736322] ERROR @wl_dev_intvar_get : error (-1)
[ 1268.736333] ERROR @wl_cfg80211_get_tx_power : error (-1)
[ 1384.957677] ERROR @wl_dev_intvar_get : error (-1)
[ 1384.957688] ERROR @wl_cfg80211_get_tx_power : error (-1)


**************** done ********************


```

Please help.

---

