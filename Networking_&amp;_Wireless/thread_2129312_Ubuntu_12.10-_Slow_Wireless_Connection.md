---
title: "Ubuntu 12.10- Slow Wireless Connection"
date: 2013-03-25
forum: Networking &amp; Wireless
---

### Post by braveswin11 on 2013-03-25
I installed Ubuntu 12.10 a while ago, and was my first upgrade ever as I upgraded from 10.10 to 12.10. However, ever since I have installed the new version, the wireless connection has been unbelievably slow considering I am getting much less than the other Windows computers at my house. I would like to know how to fix this problem, and if any more info is needed, I will get it. Also, I have noticed that sometimes the network manager doesn't show any networks, and it only gets fixed if I restart the computer.  Help me please :confused:

---

### Post by wildmanne39 on 2013-03-25
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.
Thanks

---

### Post by braveswin11 on 2013-03-25
```

*************** info trace ****************



**** uname -a ****


Linux Baasim-Laptop 3.5.0-25-generic #39-Ubuntu SMP Mon Feb 25 19:02:34 UTC 2013 i686 athlon i686 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"


**** lspci ****


02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: AMBIT Microsystem Corp. AR5BXB63 802.11bg NIC [1468:0428]
    Kernel driver in use: ath5k
--
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Gateway 2000 Device [107b:0184]
    Kernel driver in use: r8169


**** lsusb ****


Bus 002 Device 002: ID 0461:4d0f Primax Electronics, Ltd HP Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


**** iwconfig ****


wlan0     IEEE 802.11bg  ESSID:"@Home6B62"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: <MAC address removed>   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:1091   Missed beacon:0



**** rfkill ****


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


**** lsmod ****


Module                  Size  Used by
nls_iso8859_1          12618  0 
usb_storage            39351  0 
arc4                   12474  2 
joydev                 17162  0 
sparse_keymap          13659  0 
snd_hda_codec_realtek    63579  1 
snd_hda_intel          32516  5 
snd_hda_codec         111548  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13273  1 snd_hda_codec
snd_pcm                80235  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13133  0 
snd_rawmidi            25383  1 snd_seq_midi
kvm_amd                54395  0 
snd_seq_midi_event     14476  1 snd_seq_midi
kvm                   357807  1 kvm_amd
snd_seq                51281  2 snd_seq_midi,snd_seq_midi_event
snd_timer              24412  2 snd_pcm,snd_seq
psmouse                84878  0 
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62146  18 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
radeon                820764  3 
serio_raw              13032  0 
k8temp                 12843  0 
soundcore              14600  1 snd
sp5100_tco             13418  0 
snd_page_alloc         14037  2 snd_hda_intel,snd_pcm
i2c_piix4              12984  0 
ttm                    75535  1 radeon
drm_kms_helper         47304  1 radeon
drm                   238811  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13198  1 radeon
ath5k                 135206  0 
video                  18895  0 
ath                    19188  1 ath5k
rfcomm                 37277  4 
bnep                   17708  2 
wmi                    18591  0 
parport_pc             31969  0 
bluetooth             183270  10 rfcomm,bnep
ppdev                  12818  0 
binfmt_misc            17261  1 
mac80211              461261  1 ath5k
shpchp                 32190  0 
ati_agp                13178  0 
mac_hid                13038  0 
cfg80211              175574  3 ath5k,ath,mac80211
lp                     13300  0 
parport                40754  3 parport_pc,ppdev,lp
hid_generic            12485  0 
usbhid                 41734  0 
hid                    82179  2 hid_generic,usbhid
pata_atiixp            13000  0 
r8169                  55977  0 


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: wlan0  [@Home6B62] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    NewEdgeMP:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    linksys:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 15 WPA
    *@Home6B62:      Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 69 WPA
    GaTech:          Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA2
    Iron Hide:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WPA
    baker net1-guest:Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19
    Belkin_N_Wireless_BFB6BB: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 9
    HOME-FA58:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 5 WPA WPA2
    baker net1:      Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    HOME-ECC8:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 2 WPA WPA2
    linksys:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 2

  IPv4 Settings:
    Address:         192.168.0.101
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             75.75.75.75
    DNS:             75.75.76.76


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off




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

[ifupdown]
managed=false


**** NetworkManager.conf-10.04 ****




**** interfaces ****


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


**** iwlist ****


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"@Home6B62"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001436f49d12
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 000940486F6D6536423632
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030109
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000C4301000000
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"NewEdgeMP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000056bc4530f9c
                    Extra: Last beacon: 1460ms ago
                    IE: Unknown: 00094E6577456467654D50
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD810050F204104A00011010440001021041000100103B00010310470010CC7515E76FE449ADEEF3E177E4E8D498102100074C696E6B7379731023000D4C696E6B7379732045323530301024000776312E302E30301042000234321054000800060050F20400011011000D4C696E6B737973204532353030100800020084103C000103
                    IE: Unknown: DD090010180201F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000006e76b312bf5
                    Extra: Last beacon: 1496ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0106
                    IE: Unknown: 2D1AEE1116FFFFFF0001000000000000000000000000030000000000
                    IE: Unknown: 3D1601050700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05040032127A
                    IE: Unknown: DD07000C4300000000
          Cell 04 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=5/70  Signal level=-105 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000006e76b3133f7
                    Extra: Last beacon: 1496ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0106
                    IE: Unknown: 2D1AEE1116FFFFFF0001000000000000000000000000030000000000
                    IE: Unknown: 3D1601050700000000000000000000000000000000000000
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
                    IE: Unknown: 0B05040032127A
                    IE: Unknown: DD07000C4300000000
          Cell 05 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a49a42de7a
                    Extra: Last beacon: 1160ms ago
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD7E0050F204104A0001101044000102103B00010310470010138140001DD211B29FFFC67E816B4BFB102100074C696E6B73797310230006526F7574657210240007575254353447321042000C435356303148354A303631341054000800060050F204000110110011576972656C6573732D4720526F75746572100800020088
                    IE: Unknown: DD090010180200F4000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"baker net1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002d5ffd11185
                    Extra: Last beacon: 1164ms ago
                    IE: Unknown: 000A62616B6572206E657431
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081500000000000000000000000000000000000000
                    IE: Unknown: DD760050F204104A0001101044000102103B00010310470010E05C49116549A83676B0E2BA2E560DAE102100074C696E6B7379731023000545313230301024000776322E302E30321042000234321054000800060050F2040001101100054531323030100800022688103C0001011049000600372A000120
                    IE: Unknown: DD090010180202F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 07 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"Iron Hide"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000036b5ab137c2
                    Extra: Last beacon: 1152ms ago
                    IE: Unknown: 000949726F6E2048696465
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001700000000000000000000000000000000000000
                    IE: Unknown: DD090010180204F0040000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 08 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:off
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005978f65160
                    Extra: Last beacon: 1244ms ago
                    IE: Unknown: 000C000000000000000000000000
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0406000200000000
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AFE1117FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1606070500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A00B400C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD1E00904C33FE1117FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406070500000000000000000000000000000000000000
                    IE: Unknown: DD06005043030000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 09 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=10/70  Signal level=-100 dBm  
                    Encryption key:on
                    ESSID:"NOBILITY"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000073cebd54d80
                    Extra: Last beacon: 1224ms ago
                    IE: Unknown: 00084E4F42494C495459
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050401020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD050050F20500
          Cell 10 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"GaTech"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005978f79b18
                    Extra: Last beacon: 1208ms ago
                    IE: Unknown: 0006476154656368
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0406000200000000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AFE1117FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1606070500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A00B400C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD1E00904C33FE1117FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406070500000000000000000000000000000000000000
                    IE: Unknown: DD06005043030000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD720050F204104A0001101044000102103B00010310470010AE575EDD83103C9D55F21DB837C0569510210005436973636F10230003574150102400033132331042000531323334351054000800060050F20400011011000647615465636810080002200C103C0001011049000600372A000120
          Cell 11 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:off
                    ESSID:"baker net1-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002d5ffd079f0
                    Extra: Last beacon: 1204ms ago
                    IE: Unknown: 001062616B6572206E6574312D6775657374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081100000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 12 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:off
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000049a148e2
                    Extra: Last beacon: 1200ms ago
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001900000000000000000000000000000000000000
                    IE: Unknown: DD930050F204104A00011010440001011041000100103B000103104700100000000000000001100000259CEACC47102100134C696E6B73797320436F72706F726174696F6E102300075752543132304E1024000776312E302E30341042000C4A555430304B3134373136331054000800060050F204000110110014576972656C65737320526F757465722857464129100800020084
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
          Cell 13 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=15/70  Signal level=-95 dBm  
                    Encryption key:off
                    ESSID:"Belkin_N_Wireless_BFB6BB"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000004dfb9aea28f
                    Extra: Last beacon: 1196ms ago
                    IE: Unknown: 001842656C6B696E5F4E5F576972656C6573735F424642364242
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1115FFFF0000010000000000000000000000000E0000000000
                    IE: Unknown: 3D1606070700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD1E00904C33EE1115FFFF0000010000000000000000000000000E0000000000
                    IE: Unknown: DD1A00904C3406070700000000000000000000000000000000000000
          Cell 14 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=10/70  Signal level=-100 dBm  
                    Encryption key:on
                    ESSID:"HOME-FA58"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000bd84341cd8
                    Extra: Last beacon: 608ms ago
                    IE: Unknown: 0009484F4D452D46413538
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0106
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1116FFFFFF0001000000000000000000000000030000000000
                    IE: Unknown: 3D160B070700000000000000000000000000000000000000
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
                    IE: Unknown: 0B0503002B127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD9D0050F204104A0001101044000101103B000103104700102880288028801880A8800026F360FA581021001852616C696E6B20546563686E6F6C6F67792C20436F72702E1023001C52616C696E6B20576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F20400011011000952616C696E6B415053100800020084103C000101



**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1


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


[   37.293548] wmi: Mapper loaded
[   37.423758] ath5k 0000:02:00.0: registered as 'phy0'
[   39.235330] acer_wmi: Acer Laptop ACPI-WMI Extras
[   39.240811] acer_wmi: Unable to detect available WMID devices
[   39.768816] ath: EEPROM regdomain: 0x65
[   39.768817] ath: EEPROM indicates we should expect a direct regpair map
[   39.768820] ath: Country alpha2 being used: 00
[   39.768821] ath: Regpair used: 0x65
[   39.781087] Registered led device: ath5k-phy0::rx
[   39.781116] Registered led device: ath5k-phy0::tx
[   39.781127] ath5k: phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   39.845717] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   39.848804] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   41.997886] wlan0: authenticate with <MAC address removed>
[   42.008387] wlan0: send auth to <MAC address removed> (try 1/3)
[   42.011753] wlan0: authenticated
[   42.036076] wlan0: associate with <MAC address removed> (try 1/3)
[   42.038729] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[   42.039184] wlan0: associated
[   42.039488] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[126882.309256] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[126882.519552] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[126882.613141] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[126944.032550] wlan0: authenticate with <MAC address removed>
[126944.045983] wlan0: send auth to <MAC address removed> (try 1/3)
[126944.047440] wlan0: authenticated
[126944.064072] wlan0: associate with <MAC address removed> (try 1/3)
[126944.066635] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=5)
[126944.067394] wlan0: associated
[126944.068081] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[141921.033205] wlan0: authenticate with <MAC address removed>
[141921.041991] wlan0: send auth to <MAC address removed> (try 1/3)
[141921.244027] wlan0: send auth to <MAC address removed> (try 2/3)
[141921.448018] wlan0: send auth to <MAC address removed> (try 3/3)
[141921.652029] wlan0: authentication with <MAC address removed> timed out
[141922.369910] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[141922.683178] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[141922.845642] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[141984.078505] wlan0: authenticate with <MAC address removed>
[141984.085222] wlan0: send auth to <MAC address removed> (try 1/3)
[141984.086705] wlan0: authenticated
[141984.112083] wlan0: associate with <MAC address removed> (try 1/3)
[141984.114460] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[141984.115201] wlan0: associated
[141984.115787] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[161492.363447] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[161492.644353] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[161492.814418] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[161554.141212] wlan0: authenticate with <MAC address removed>
[161554.154310] wlan0: send auth to <MAC address removed> (try 1/3)
[161554.155927] wlan0: authenticated
[161554.176084] wlan0: associate with <MAC address removed> (try 1/3)
[161554.178476] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=5)
[161554.179256] wlan0: associated
[161554.179888] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[315097.260066] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[315097.504255] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[315097.611191] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[315159.041775] wlan0: authenticate with <MAC address removed>
[315159.052634] wlan0: send auth to <MAC address removed> (try 1/3)
[315159.055051] wlan0: authenticated
[315159.072091] wlan0: associate with <MAC address removed> (try 1/3)
[315159.075578] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=5)
[315159.076368] wlan0: associated
[315159.077464] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[328241.037996] wlan0: authenticate with <MAC address removed>
[328241.059335] wlan0: send auth to <MAC address removed> (try 1/3)
[328241.260045] wlan0: send auth to <MAC address removed> (try 2/3)
[328241.464019] wlan0: send auth to <MAC address removed> (try 3/3)
[328241.668032] wlan0: authentication with <MAC address removed> timed out
[328242.253067] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[328242.539948] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[328242.776931] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[328304.110537] wlan0: authenticate with <MAC address removed>
[328304.119311] wlan0: send auth to <MAC address removed> (try 1/3)
[328304.120963] wlan0: authenticated
[328304.140078] wlan0: associate with <MAC address removed> (try 1/3)
[328304.142809] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[328304.143560] wlan0: associated
[328304.144240] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[498487.332054] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[498487.566289] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[498487.640698] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[498549.069204] wlan0: authenticate with <MAC address removed>
[498549.074335] wlan0: send auth to <MAC address removed> (try 1/3)
[498549.075796] wlan0: authenticated
[498549.093485] wlan0: associate with <MAC address removed> (try 1/3)
[498549.095873] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[498549.096654] wlan0: associated
[498549.097703] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[862102.413889] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[862102.832742] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[862103.102172] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[862164.148497] wlan0: authenticate with <MAC address removed>
[862164.159435] wlan0: send auth to <MAC address removed> (try 1/3)
[862164.161011] wlan0: authenticated
[862164.180085] wlan0: associate with <MAC address removed> (try 1/3)
[862164.182522] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[862164.183301] wlan0: associated
[862164.183926] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


**************** done ********************


```

The attachment was too large to upload.

---

### Post by wildmanne39 on 2013-03-25
Please do:
```
echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k

```
Set your wireless setting to match the screenshots.
Thanks

---

### Post by braveswin11 on 2013-03-25
I did those commands, and matched the settings. What should I do next?

---

### Post by sammiev on 2013-03-25
> **braveswin11 said:**
> I did those commands, and matched the settings. What should I do next?

Close your browser and try it again. Should work after that.

---

### Post by wildmanne39 on 2013-03-26
Hi, for the wireless settings to take effect you may have to reboot but changes made by the commands should work immediately.
Thanks

---

### Post by braveswin11 on 2013-03-29
Well, I believe this problem still hasn't been fixed. I got an email from my internet provider which stated that my speed got enhanced. I was excited, so I followed their steps, and tested the speeds on my windows computer and ubuntu. I would also like to say that my ubuntu computer is closer to my router. I saw the speeds definitely increase to about 15 mb/s for download and 10 mb/s for upload on the windows computer. However, on the ubuntu, I still only see 5 mb/s download yet I also get 10 mb/s upload. Is my download speed getting held back because it never goes above 5 mb/s?

---

### Post by braveswin11 on 2013-04-07
Going to bump this as it's still going on.

On the ubuntu computer: Your Speed Result:Download Speed: 3827 kbps (478.4 KB/sec transfer rate)
Upload Speed: 8999 kbps (1124.9 KB/sec transfer rate)

On the windows computer I get at least 12000 kbps for download speed, but I get about the same upload speed. Any ideas because this is getting annoying.

---

### Post by wildmanne39 on 2013-04-07
Go into your router and change your encryption to just wpa2 if you have that option it usually works better, and change your channel to 1 or 11.
Thanks

---

