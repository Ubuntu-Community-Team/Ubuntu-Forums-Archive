---
title: "Connecting to D-Link Wireless Router"
date: 2012-04-21
forum: Networking &amp; Wireless
---

### Post by markaokeeffe on 2012-04-21
I have installed ubuntu 11.10 and now upgraded to 12.04 final beta. I have a problem connecting to my wireless router at home. I can connect to any other router however it will not pick up my D-Link router at home. I can connect via cable no problem. I have installed all relevant drivers, I think. There is no problem in windows. I have reinstalled ubuntu, upgraded etc. and still no luck. Any help would be lovely :)

---

### Post by wildmanne39 on 2012-04-21
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by markaokeeffe on 2012-04-21
I am connected to a different wireless router at the moment just in case that shows up in the code

```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux marks-laptop 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
mark@marks-laptop:~$ lspci -nnk | grep -iA2 net
04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
	Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
	Kernel driver in use: wl
--
09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
	Subsystem: Dell Device [1028:0413]
	Kernel driver in use: r8169
mark@marks-laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0c45:6417 Microdia Integrated Webcam
mark@marks-laptop:~$ iwconfig
lo        no wireless extensions.

eth2      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:214  Noise level:199
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.

mark@marks-laptop:~$ rfkill list all
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
mark@marks-laptop:~$ lsmod
Module                  Size  Used by
michael_mic            12612  8 
arc4                   12529  4 
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
joydev                 17693  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  20 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lib80211_crypt_tkip    17390  0 
uvcvideo               72627  0 
wl                   2568210  0 
videodev               98259  1 uvcvideo
radeon                804372  3 
psmouse                87603  0 
v4l2_compat_ioctl32    17128  1 videodev
ttm                    76949  1 radeon
drm_kms_helper         46978  1 radeon
drm                   242038  5 radeon,ttm,drm_kms_helper
mac_hid                13253  0 
dell_laptop            18119  0 
dell_wmi               12681  0 
i2c_algo_bit           13423  1 radeon
sparse_keymap          13890  1 dell_wmi
soundcore              15091  1 snd
video                  19596  0 
lp                     17799  0 
serio_raw              13211  0 
dcdbas                 14490  1 dell_laptop
parport                46562  3 parport_pc,ppdev,lp
wmi                    19256  1 dell_wmi
lib80211               14381  2 lib80211_crypt_tkip,wl
mei                    41616  0 
intel_ips              18089  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
usbhid                 47199  0 
hid                    99559  1 usbhid
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
firewire_ohci          41000  0 
firewire_core          63558  7 firewire_ohci
r8169                  62099  0 
crc_itu_t              12707  1 firewire_core
```

---

### Post by wildmanne39 on 2012-04-21
Hi, I recommend we change drivers please do:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then
```
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
```
Reboot, thanks

---

### Post by markaokeeffe on 2012-04-21
Yes! It works now, thank you so much! You're a genius, I've looked through multiple forums to try and find a solution, thanks so much!

---

### Post by wildmanne39 on 2012-04-21
Hi, your welcome! please use thread tools at the top of the page to mark the thread solved.
Thanks

---

### Post by markaokeeffe on 2012-04-22
Unfortunately, the problem is not fully fixed as I previously thought. Ubuntu is now recognizing the dlink router and it tells me that there is a connection established however there is no internet access. I have tried to connect to a router that I previously had no problem with, and it's the same story. I wonder could you help me with this? Thanks.

---

### Post by wildmanne39 on 2012-04-22
Hi, please post the output of:
```
nm-tool
sudo iwlist scan
lsmod | grep b43
```
```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e wlan -e etork | tail -n55
```
Thanks

---

### Post by markaokeeffe on 2012-04-22
```
mark@marks-laptop:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        F0:4D:A2:57:DF:3F

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.187
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


- Device: wlan0  [dlink] -------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             connecting (configuring)
  Default:           no
  HW Address:        78:E4:00:E2:99:02

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Cablesurf_338d46:Infra, 00:18:F3:E6:12:F9, Freq 2412 MHz, Rate 54 Mb/s, Strength 65 WPA
    vodafoneSecure_218C: Infra, 06:0C:C3:54:21:8C, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    BTVOYAGER2110-0C:Infra, 00:24:D2:80:2E:0C, Freq 2417 MHz, Rate 54 Mb/s, Strength 44 WEP
    vodafone_218C:   Infra, 00:0C:C3:54:21:8C, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WEP
    Solar BB:        Infra, 94:0C:6D:EE:06:CE, Freq 2427 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    dlink:           Infra, 00:21:91:EC:BC:FE, Freq 2467 MHz, Rate 54 Mb/s, Strength 100 WEP


mark@marks-laptop:~$ sudo iwlist scan
[sudo] password for mark: 
Sorry, try again.
[sudo] password for mark: 
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:24:D2:80:2E:0C
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"BTVOYAGER2110-0C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000af4c1ad18b
                    Extra: Last beacon: 1008ms ago
                    IE: Unknown: 00104254564F5941474552323131302D3043
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030102
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180201F1
          Cell 02 - Address: 00:18:F3:E6:12:F9
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"Cablesurf_338d46"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000011a1ff4d188
                    Extra: Last beacon: 920ms ago
                    IE: Unknown: 00104361626C65737572665F333338643436
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD090010180201F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: 94:0C:6D:EE:06:CE
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"Solar BB"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000112367181
                    Extra: Last beacon: 11996ms ago
                    IE: Unknown: 0008536F6C6172204242
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030104
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0900037F01010008FF7F
                    IE: Unknown: DD1A00037F0301000000940C6DEE06CE960C6DEE06CE64002C010808
          Cell 04 - Address: 00:0C:C3:54:21:8C
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key:on
                    ESSID:"vodafone_218C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000077fc05f586
                    Extra: Last beacon: 4640ms ago
                    IE: Unknown: 000D766F6461666F6E655F32313843
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: 0706465220010D14
          Cell 05 - Address: 06:0C:C3:54:21:8C
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"vodafoneSecure_218C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000077fc05f584
                    Extra: Last beacon: 4588ms ago
                    IE: Unknown: 0013766F6461666F6E655365637572655F32313843
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101040003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: 0706465220010D14
                    IE: Unknown: DD2C0050F204104A00011010440001021057000100104700105BB95DFD1E594BBD89E54302EA147344103C000101
          Cell 06 - Address: 00:21:91:EC:BC:FE
                    Channel:12
                    Frequency:2.467 GHz (Channel 12)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"dlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000004553132c180
                    Extra: Last beacon: 44ms ago
                    IE: Unknown: 0005646C696E6B
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010C
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD070050F202000100
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160C001B0000000F000000000000000000000000000000
                    IE: Unknown: DD1E00904C336C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340C00030000000F000000000000000000000000000000
                    IE: Unknown: 050400010000
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD130050F204104A0001101044000102103C000103

eth0      Interface doesn't support scanning.

```


```
Apr 22 20:11:12 marks-laptop wpa_supplicant[1547]: Trying to authenticate with 00:21:91:ec:bc:fe (SSID='dlink' freq=2467 MHz)
Apr 22 20:11:12 marks-laptop NetworkManager[872]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Apr 22 20:11:12 marks-laptop kernel: [ 1541.786856] wlan0: direct probe to 00:21:91:ec:bc:fe (try 1/3)
Apr 22 20:11:12 marks-laptop kernel: [ 1541.985291] wlan0: direct probe to 00:21:91:ec:bc:fe (try 2/3)
Apr 22 20:11:12 marks-laptop kernel: [ 1542.184967] wlan0: direct probe to 00:21:91:ec:bc:fe (try 3/3)
Apr 22 20:11:12 marks-laptop kernel: [ 1542.384599] wlan0: direct probe to 00:21:91:ec:bc:fe timed out
Apr 22 20:11:19 marks-laptop wpa_supplicant[1547]: Trying to authenticate with 00:21:91:ec:bc:fe (SSID='dlink' freq=2467 MHz)
Apr 22 20:11:19 marks-laptop kernel: [ 1548.624008] wlan0: direct probe to 00:21:91:ec:bc:fe (try 1/3)
Apr 22 20:11:19 marks-laptop kernel: [ 1548.821493] wlan0: direct probe to 00:21:91:ec:bc:fe (try 2/3)
Apr 22 20:11:19 marks-laptop kernel: [ 1549.021164] wlan0: direct probe to 00:21:91:ec:bc:fe (try 3/3)
Apr 22 20:11:19 marks-laptop kernel: [ 1549.220835] wlan0: direct probe to 00:21:91:ec:bc:fe timed out
Apr 22 20:11:26 marks-laptop wpa_supplicant[1547]: Trying to authenticate with 00:21:91:ec:bc:fe (SSID='dlink' freq=2467 MHz)
Apr 22 20:11:26 marks-laptop kernel: [ 1555.494831] wlan0: direct probe to 00:21:91:ec:bc:fe (try 1/3)
Apr 22 20:11:26 marks-laptop kernel: [ 1555.693666] wlan0: direct probe to 00:21:91:ec:bc:fe (try 2/3)
Apr 22 20:11:26 marks-laptop kernel: [ 1555.893369] wlan0: direct probe to 00:21:91:ec:bc:fe (try 3/3)
Apr 22 20:11:26 marks-laptop kernel: [ 1556.092965] wlan0: direct probe to 00:21:91:ec:bc:fe timed out
Apr 22 20:11:32 marks-laptop wpa_supplicant[1547]: Trying to authenticate with 00:21:91:ec:bc:fe (SSID='dlink' freq=2467 MHz)
Apr 22 20:11:32 marks-laptop kernel: [ 1562.359550] wlan0: direct probe to 00:21:91:ec:bc:fe (try 1/3)
Apr 22 20:11:33 marks-laptop kernel: [ 1562.557848] wlan0: direct probe to 00:21:91:ec:bc:fe (try 2/3)
Apr 22 20:11:33 marks-laptop kernel: [ 1562.757526] wlan0: direct probe to 00:21:91:ec:bc:fe (try 3/3)
Apr 22 20:11:33 marks-laptop kernel: [ 1562.957125] wlan0: direct probe to 00:21:91:ec:bc:fe timed out
Apr 22 20:11:39 marks-laptop wpa_supplicant[1547]: Trying to authenticate with 00:21:91:ec:bc:fe (SSID='dlink' freq=2467 MHz)
Apr 22 20:11:39 marks-laptop kernel: [ 1569.215326] wlan0: direct probe to 00:21:91:ec:bc:fe (try 1/3)
Apr 22 20:11:39 marks-laptop kernel: [ 1569.414010] wlan0: direct probe to 00:21:91:ec:bc:fe (try 2/3)
Apr 22 20:11:40 marks-laptop kernel: [ 1569.613698] wlan0: direct probe to 00:21:91:ec:bc:fe (try 3/3)
Apr 22 20:11:40 marks-laptop kernel: [ 1569.813309] wlan0: direct probe to 00:21:91:ec:bc:fe timed out
Apr 22 20:11:46 marks-laptop wpa_supplicant[1547]: Trying to authenticate with 00:21:91:ec:bc:fe (SSID='dlink' freq=2467 MHz)
Apr 22 20:11:46 marks-laptop kernel: [ 1576.087546] wlan0: direct probe to 00:21:91:ec:bc:fe (try 1/3)
Apr 22 20:11:46 marks-laptop kernel: [ 1576.286243] wlan0: direct probe to 00:21:91:ec:bc:fe (try 2/3)
Apr 22 20:11:47 marks-laptop kernel: [ 1576.485855] wlan0: direct probe to 00:21:91:ec:bc:fe (try 3/3)
Apr 22 20:11:47 marks-laptop kernel: [ 1576.685503] wlan0: direct probe to 00:21:91:ec:bc:fe timed out
Apr 22 20:11:53 marks-laptop wpa_supplicant[1547]: Trying to authenticate with 00:21:91:ec:bc:fe (SSID='dlink' freq=2467 MHz)
Apr 22 20:11:53 marks-laptop kernel: [ 1582.907794] wlan0: direct probe to 00:21:91:ec:bc:fe (try 1/3)
Apr 22 20:11:53 marks-laptop kernel: [ 1583.106535] wlan0: direct probe to 00:21:91:ec:bc:fe (try 2/3)
Apr 22 20:11:53 marks-laptop kernel: [ 1583.306073] wlan0: direct probe to 00:21:91:ec:bc:fe (try 3/3)
Apr 22 20:11:54 marks-laptop kernel: [ 1583.505755] wlan0: direct probe to 00:21:91:ec:bc:fe timed out
Apr 22 20:12:00 marks-laptop wpa_supplicant[1547]: Trying to authenticate with 00:21:91:ec:bc:fe (SSID='dlink' freq=2467 MHz)
Apr 22 20:12:00 marks-laptop kernel: [ 1589.779971] wlan0: direct probe to 00:21:91:ec:bc:fe (try 1/3)
Apr 22 20:12:00 marks-laptop kernel: [ 1589.978546] wlan0: direct probe to 00:21:91:ec:bc:fe (try 2/3)
Apr 22 20:12:00 marks-laptop kernel: [ 1590.178202] wlan0: direct probe to 00:21:91:ec:bc:fe (try 3/3)
Apr 22 20:12:00 marks-laptop kernel: [ 1590.377873] wlan0: direct probe to 00:21:91:ec:bc:fe timed out
Apr 22 20:12:07 marks-laptop wpa_supplicant[1547]: Trying to authenticate with 00:21:91:ec:bc:fe (SSID='dlink' freq=2467 MHz)
Apr 22 20:12:07 marks-laptop kernel: [ 1596.640179] wlan0: direct probe to 00:21:91:ec:bc:fe (try 1/3)
Apr 22 20:12:07 marks-laptop kernel: [ 1596.838753] wlan0: direct probe to 00:21:91:ec:bc:fe (try 2/3)
Apr 22 20:12:07 marks-laptop kernel: [ 1597.038388] wlan0: direct probe to 00:21:91:ec:bc:fe (try 3/3)
Apr 22 20:12:07 marks-laptop kernel: [ 1597.238086] wlan0: direct probe to 00:21:91:ec:bc:fe timed out
Apr 22 20:12:11 marks-laptop NetworkManager[872]: <warn> Activation (wlan0/wireless): association took too long.
Apr 22 20:12:11 marks-laptop NetworkManager[872]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Apr 22 20:12:11 marks-laptop NetworkManager[872]: <warn> Activation (wlan0/wireless): asking for new secrets
Apr 22 20:12:11 marks-laptop NetworkManager[872]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Apr 22 20:12:13 marks-laptop NetworkManager[872]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Apr 22 20:12:13 marks-laptop NetworkManager[872]: <warn> Activation (wlan0) failed for access point (dlink)
Apr 22 20:12:13 marks-laptop NetworkManager[872]: <warn> Activation (wlan0) failed.
Apr 22 20:12:13 marks-laptop NetworkManager[872]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Apr 22 20:12:13 marks-laptop NetworkManager[872]: <info> (wlan0): deactivating device (reason 'none') [0]
```

---

### Post by wildmanne39 on 2012-04-22
Hi, disable your encryption for a minute and see if it works, then change it to just wpa2 if you have that option it works best with linux.
Thanks

---

### Post by markaokeeffe on 2012-04-22
I'm sorry I'm a serious noob to this, what exactly do you want me to do?

---

### Post by wildmanne39 on 2012-04-22
Hi, open your browser and type 192.168.0.1 and hopefully it will bring up your router settings, but you need to be connected by ethernet connection first then look for security settings and change wep to wpa2 and save.
Thanks

---

### Post by markaokeeffe on 2012-04-22
I've changed it to WPA2 now but unfortunately still no luck, it still establishes a connection but no internet connection once I try to access any website.

---

### Post by wildmanne39 on 2012-04-22
Hi, check and make sure your settings in network manager at the right top of the screen is also set to wpa and not wep, then reboot and if it does not connect post the output of:
```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e wlan -e etork | tail -n55
```
again since you have changed the settings.
Thanks

---

### Post by markaokeeffe on 2012-04-22
Yes it is set to wpa ```
Apr 22 22:43:44 marks-laptop NetworkManager[867]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Apr 22 22:43:44 marks-laptop NetworkManager[867]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 22 22:43:44 marks-laptop NetworkManager[867]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 22 22:43:44 marks-laptop NetworkManager[867]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 22 22:43:44 marks-laptop NetworkManager[867]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 22 22:43:44 marks-laptop NetworkManager[867]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 22 22:43:44 marks-laptop NetworkManager[867]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr 22 22:43:44 marks-laptop NetworkManager[867]: <info> Activation (wlan0/wireless): connection 'dlink 1' has security, and secrets exist.  No new secrets needed.
Apr 22 22:43:44 marks-laptop NetworkManager[867]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 22 22:43:44 marks-laptop NetworkManager[867]: <info> (wlan0): supplicant interface state: inactive -> scanning
Apr 22 22:43:45 marks-laptop wpa_supplicant[1548]: Trying to authenticate with 00:21:91:ec:bc:fe (SSID='dlink' freq=2467 MHz)
Apr 22 22:43:45 marks-laptop NetworkManager[867]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Apr 22 22:43:45 marks-laptop wpa_supplicant[1548]: Trying to associate with 00:21:91:ec:bc:fe (SSID='dlink' freq=2467 MHz)
Apr 22 22:43:45 marks-laptop kernel: [   23.448073] wlan0: authenticate with 00:21:91:ec:bc:fe (try 1)
Apr 22 22:43:45 marks-laptop kernel: [   23.449706] wlan0: authenticated
Apr 22 22:43:45 marks-laptop NetworkManager[867]: <info> (wlan0): supplicant interface state: authenticating -> associating
Apr 22 22:43:45 marks-laptop kernel: [   23.472006] wlan0: associate with 00:21:91:ec:bc:fe (try 1)
Apr 22 22:43:45 marks-laptop kernel: [   23.474917] wlan0: RX AssocResp from 00:21:91:ec:bc:fe (capab=0x431 status=0 aid=1)
Apr 22 22:43:45 marks-laptop kernel: [   23.474924] wlan0: associated
Apr 22 22:43:45 marks-laptop wpa_supplicant[1548]: Associated with 00:21:91:ec:bc:fe
Apr 22 22:43:45 marks-laptop kernel: [   23.476321] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Apr 22 22:43:45 marks-laptop wpa_supplicant[1548]: WPA: Key negotiation completed with 00:21:91:ec:bc:fe [PTK=CCMP GTK=TKIP]
Apr 22 22:43:45 marks-laptop wpa_supplicant[1548]: CTRL-EVENT-CONNECTED - Connection to 00:21:91:ec:bc:fe completed (auth) [id=0 id_str=]
Apr 22 22:43:45 marks-laptop NetworkManager[867]: <info> (wlan0): supplicant interface state: associating -> completed
Apr 22 22:43:45 marks-laptop NetworkManager[867]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'dlink'.
Apr 22 22:43:45 marks-laptop NetworkManager[867]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr 22 22:43:45 marks-laptop NetworkManager[867]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Apr 22 22:43:45 marks-laptop NetworkManager[867]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Apr 22 22:43:45 marks-laptop NetworkManager[867]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Apr 22 22:43:45 marks-laptop NetworkManager[867]: <info> Activation (wlan0) Beginning IP6 addrconf.
Apr 22 22:43:45 marks-laptop NetworkManager[867]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Apr 22 22:43:46 marks-laptop NetworkManager[867]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Apr 22 22:43:46 marks-laptop dhclient: Listening on LPF/wlan0/78:e4:00:e2:99:02
Apr 22 22:43:46 marks-laptop dhclient: Sending on   LPF/wlan0/78:e4:00:e2:99:02
Apr 22 22:43:46 marks-laptop dhclient: DHCPREQUEST of 192.168.0.170 on wlan0 to 255.255.255.255 port 67
Apr 22 22:43:46 marks-laptop NetworkManager[867]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Apr 22 22:43:46 marks-laptop NetworkManager[867]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Apr 22 22:43:46 marks-laptop NetworkManager[867]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Apr 22 22:43:46 marks-laptop avahi-daemon[884]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.170.
Apr 22 22:43:46 marks-laptop avahi-daemon[884]: New relevant interface wlan0.IPv4 for mDNS.
Apr 22 22:43:46 marks-laptop avahi-daemon[884]: Registering new address record for 192.168.0.170 on wlan0.IPv4.
Apr 22 22:43:47 marks-laptop avahi-daemon[884]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::7ae4:ff:fee2:9902.
Apr 22 22:43:47 marks-laptop avahi-daemon[884]: New relevant interface wlan0.IPv6 for mDNS.
Apr 22 22:43:47 marks-laptop avahi-daemon[884]: Registering new address record for fe80::7ae4:ff:fee2:9902 on wlan0.*.
Apr 22 22:43:47 marks-laptop NetworkManager[867]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Apr 22 22:43:56 marks-laptop kernel: [   33.754156] wlan0: no IPv6 routers present
Apr 22 22:43:57 marks-laptop NetworkManager[867]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Apr 22 22:43:57 marks-laptop NetworkManager[867]: <info> Policy set 'dlink 1' (wlan0) as default for IPv4 routing and DNS.
Apr 22 22:43:57 marks-laptop NetworkManager[867]: <info> Activation (wlan0) successful, device activated.
Apr 22 22:43:57 marks-laptop NetworkManager[867]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Apr 22 22:44:06 marks-laptop NetworkManager[867]: <info> (wlan0): IP6 addrconf timed out or failed.
Apr 22 22:44:06 marks-laptop NetworkManager[867]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Apr 22 22:44:06 marks-laptop NetworkManager[867]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Apr 22 22:44:06 marks-laptop NetworkManager[867]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Apr 22 22:44:39 marks-laptop NetworkManager[867]: <info> Policy set 'dlink 1' (wlan0) as default for IPv4 routing and DNS.
```

---

### Post by wildmanne39 on 2012-04-22
Hi, please set your wireless settings to match the screenshots.

I have been researching and this is a known issue I will try an experiment and see if it works.

Please try:
```
sudo ifconfig wlan0 down
sudo rmmod -f b43
sudo modprobe b43 nohwcrypt=1
sudo ifconfig wlan0 up

```
if it works do not reboot we will need to make it permanent, if it does not then reboot.
Thanks

---

### Post by markaokeeffe on 2012-04-22
I did all that and tried again but the same problem so I rebooted, still the same problem. Thanks.

---

### Post by wildmanne39 on 2012-04-22
When you ran the commands I gave you in my last post did you get any errors?
Thanks

---

### Post by markaokeeffe on 2012-04-22
No, but I didn't receive any feedback from the terminal, was I supposed to?

---

### Post by wildmanne39 on 2012-04-22
Hi, with those commands no output means no errors since that is the case please run the commands again and do not reboot and let's see if we can fix this issue by posting the output of:
```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e wlan -e etork | tail -n55
```
again I am looking for a change in the error messages, I believe we have more then one issue and we need to take care of them one at a time.
Thanks

---

### Post by markaokeeffe on 2012-04-22
Here is the output, thanks!


```
Apr 22 23:49:22 marks-laptop NetworkManager[857]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 22 23:49:22 marks-laptop NetworkManager[857]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 22 23:49:22 marks-laptop NetworkManager[857]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 22 23:49:22 marks-laptop NetworkManager[857]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr 22 23:49:22 marks-laptop NetworkManager[857]: <info> Activation (wlan0/wireless): access point 'Home' has security, but secrets are required.
Apr 22 23:49:22 marks-laptop NetworkManager[857]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Apr 22 23:49:22 marks-laptop NetworkManager[857]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 22 23:49:22 marks-laptop NetworkManager[857]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 22 23:49:22 marks-laptop NetworkManager[857]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 22 23:49:22 marks-laptop NetworkManager[857]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Apr 22 23:49:22 marks-laptop NetworkManager[857]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 22 23:49:22 marks-laptop NetworkManager[857]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 22 23:49:22 marks-laptop NetworkManager[857]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 22 23:49:22 marks-laptop NetworkManager[857]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr 22 23:49:22 marks-laptop NetworkManager[857]: <info> Activation (wlan0/wireless): connection 'Home' has security, and secrets exist.  No new secrets needed.
Apr 22 23:49:22 marks-laptop NetworkManager[857]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 22 23:49:23 marks-laptop NetworkManager[857]: <info> (wlan0): supplicant interface state: inactive -> scanning
Apr 22 23:49:24 marks-laptop wpa_supplicant[1556]: Trying to authenticate with 00:21:91:ec:bc:fe (SSID='dlink' freq=2467 MHz)
Apr 22 23:49:24 marks-laptop NetworkManager[857]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Apr 22 23:49:24 marks-laptop wpa_supplicant[1556]: Trying to associate with 00:21:91:ec:bc:fe (SSID='dlink' freq=2467 MHz)
Apr 22 23:49:24 marks-laptop kernel: [  102.748410] wlan0: authenticate with 00:21:91:ec:bc:fe (try 1)
Apr 22 23:49:24 marks-laptop kernel: [  102.750355] wlan0: authenticated
Apr 22 23:49:24 marks-laptop NetworkManager[857]: <info> (wlan0): supplicant interface state: authenticating -> associating
Apr 22 23:49:24 marks-laptop kernel: [  102.772376] wlan0: associate with 00:21:91:ec:bc:fe (try 1)
Apr 22 23:49:24 marks-laptop kernel: [  102.775330] wlan0: RX AssocResp from 00:21:91:ec:bc:fe (capab=0x431 status=0 aid=1)
Apr 22 23:49:24 marks-laptop kernel: [  102.775336] wlan0: associated
Apr 22 23:49:24 marks-laptop wpa_supplicant[1556]: Associated with 00:21:91:ec:bc:fe
Apr 22 23:49:24 marks-laptop kernel: [  102.777363] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Apr 22 23:49:24 marks-laptop wpa_supplicant[1556]: WPA: Key negotiation completed with 00:21:91:ec:bc:fe [PTK=CCMP GTK=TKIP]
Apr 22 23:49:24 marks-laptop wpa_supplicant[1556]: CTRL-EVENT-CONNECTED - Connection to 00:21:91:ec:bc:fe completed (auth) [id=0 id_str=]
Apr 22 23:49:24 marks-laptop NetworkManager[857]: <info> (wlan0): supplicant interface state: associating -> completed
Apr 22 23:49:24 marks-laptop NetworkManager[857]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'dlink'.
Apr 22 23:49:24 marks-laptop NetworkManager[857]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr 22 23:49:24 marks-laptop NetworkManager[857]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Apr 22 23:49:24 marks-laptop NetworkManager[857]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Apr 22 23:49:24 marks-laptop NetworkManager[857]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Apr 22 23:49:24 marks-laptop NetworkManager[857]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Apr 22 23:49:24 marks-laptop NetworkManager[857]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Apr 22 23:49:24 marks-laptop dhclient: Listening on LPF/wlan0/78:e4:00:e2:99:02
Apr 22 23:49:24 marks-laptop dhclient: Sending on   LPF/wlan0/78:e4:00:e2:99:02
Apr 22 23:49:24 marks-laptop dhclient: DHCPREQUEST of 192.168.0.170 on wlan0 to 255.255.255.255 port 67
Apr 22 23:49:24 marks-laptop NetworkManager[857]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Apr 22 23:49:24 marks-laptop NetworkManager[857]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Apr 22 23:49:24 marks-laptop NetworkManager[857]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Apr 22 23:49:24 marks-laptop avahi-daemon[895]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.170.
Apr 22 23:49:24 marks-laptop avahi-daemon[895]: New relevant interface wlan0.IPv4 for mDNS.
Apr 22 23:49:24 marks-laptop avahi-daemon[895]: Registering new address record for 192.168.0.170 on wlan0.IPv4.
Apr 22 23:49:25 marks-laptop NetworkManager[857]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Apr 22 23:49:25 marks-laptop NetworkManager[857]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Apr 22 23:49:25 marks-laptop NetworkManager[857]: <info> Policy set 'Home' (wlan0) as default for IPv4 routing and DNS.
Apr 22 23:49:25 marks-laptop NetworkManager[857]: <info> Activation (wlan0) successful, device activated.
Apr 22 23:49:25 marks-laptop NetworkManager[857]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Apr 22 23:49:26 marks-laptop avahi-daemon[895]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::7ae4:ff:fee2:9902.
Apr 22 23:49:26 marks-laptop avahi-daemon[895]: New relevant interface wlan0.IPv6 for mDNS.
Apr 22 23:49:26 marks-laptop avahi-daemon[895]: Registering new address record for fe80::7ae4:ff:fee2:9902 on wlan0.*.
```

---

### Post by wildmanne39 on 2012-04-22
Hi, I do not know if we can get around this bug or not.

Your wireless tried to connect to a network called home before it tried dlink this time.

You did set IPV6 to ignore correct?

When could install the other driver and start over or we could install wicd and uninstall network manager one of those options may fix it, let me know which you want to try first.
Thanks

---

### Post by markaokeeffe on 2012-04-22
Sorry that was very stupid of me, when I was the wireless settings I changed the connection name of dlink to "Home". Sorry, that probably added some unnecessary confusion. Possibly installing the other driver might be the best route, what do you think?

---

### Post by wildmanne39 on 2012-04-22
Hi, it is hard to say it is possible since you changed your encryption that it might connect using the other driver but I found several posts about this issue using google and none of them were solved.

Let's try this before we switch:
```
sudo modprobe -r b43 nohwcrypt=1
sudo modprobe b43 pio=1
sudo iwlist wlan0 scan
```
Thanks

---

### Post by markaokeeffe on 2012-04-22
This is what I got: ```
mark@marks-laptop:~$ sudo modprobe -r b43 nohwcrypt=1
[sudo] password for mark: 
FATAL: Module nohwcrypt=1 not found.
mark@marks-laptop:~$ sudo modprobe b43 pio=1
mark@marks-laptop:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:18:F3:E6:12:F9
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"Cablesurf_338d46"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000011db770574c
                    Extra: Last beacon: 5404ms ago
                    IE: Unknown: 00104361626C65737572665F333338643436
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD090010180201F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: 00:24:D2:80:2E:0C
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"BTVOYAGER2110-0C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000b2e37a3188
                    Extra: Last beacon: 7376ms ago
                    IE: Unknown: 00104254564F5941474552323131302D3043
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030102
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180201F1
          Cell 03 - Address: 00:21:91:EC:BC:FE
                    Channel:12
                    Frequency:2.467 GHz (Channel 12)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"dlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002e16d4180
                    Extra: Last beacon: 4572ms ago
                    IE: Unknown: 0005646C696E6B
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010C
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160C001B0000000F000000000000000000000000000000
                    IE: Unknown: DD1E00904C336C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340C00030000000F000000000000000000000000000000
          Cell 04 - Address: 06:0C:C3:54:21:8C
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"vodafoneSecure_218C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001e95663e0
                    Extra: Last beacon: 4840ms ago
                    IE: Unknown: 0013766F6461666F6E655365637572655F32313843
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
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
                    IE: Unknown: DD180050F2020101040003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: 0706465220010D14
                    IE: Unknown: DDB30050F204104A000110104400010210570001001041000100103B000103104700105BB95DFD1E594BBD89E54302EA14734410210005426577616E1023002A76662D4152563435313050572D412D4C462D4C332D566F6461666F6E655F4945307830304135313430361024000A307830304135313430361042000F3433303030303035353133363132311054000800060050F20400011011000F496E66696E656F6E2044616E756265100800020080103C000101
          Cell 05 - Address: 00:0C:C3:54:21:8C
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"vodafone_218C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001e9571982
                    Extra: Last beacon: 4848ms ago
                    IE: Unknown: 000D766F6461666F6E655F32313843
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101040003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: 0706465220010D14

```

Thanks!

---

### Post by wildmanne39 on 2012-04-23
Hi, let's switch drivers please do:
```
sudo apt-get purge b43-fwcutter firmware-b43-lpphy-installer
```
```
sudo apt-get install bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
then reboot.
Thanks

---

### Post by markaokeeffe on 2012-04-23
Hi again, I did that and I have rebooted. Now it is back to the original problem, it cannot find the dlink router.

Thanks.

---

### Post by wildmanne39 on 2012-04-23
Hi, okay that is what I figured I did not think it would be that easy please post the output of:
```
iwconfig
rfkill list all
lsmod
nm-tool
sudo iwlist scan
```
```
sudo cat /var/log/syslog | grep -e wl -e firmware -e eth1 -e wpa -e etork | tail -n55
```
Thanks

---

### Post by markaokeeffe on 2012-04-23
```
mark@marks-laptop:~$ iwconfig
lo        no wireless extensions.

eth2      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.

mark@marks-laptop:~$ rfkill list all
0: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
mark@marks-laptop:~$ lsmod
Module                  Size  Used by
joydev                 17693  0 
parport_pc             32866  0 
ppdev                  17113  0 
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
snd_hda_codec_hdmi     32474  1 
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
snd_hda_codec_idt      70795  1 
dell_laptop            18119  0 
dcdbas                 14490  1 dell_laptop
snd_hda_intel          33773  7 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
lib80211_crypt_tkip    17390  0 
wmi                    19256  1 dell_wmi
snd_timer              29990  2 snd_pcm,snd_seq
video                  19596  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                87603  0 
serio_raw              13211  0 
wl                   2568210  0 
mei                    41616  0 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
radeon                804372  3 
ttm                    76949  1 radeon
drm_kms_helper         46978  1 radeon
v4l2_compat_ioctl32    17128  1 videodev
intel_ips              18089  0 
snd                    78855  23 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   242038  5 radeon,ttm,drm_kms_helper
mac_hid                13253  0 
i2c_algo_bit           13423  1 radeon
lib80211               14381  2 lib80211_crypt_tkip,wl
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  62099  0 
firewire_ohci          41000  0 
sdhci_pci              18826  0 
firewire_core          63558  1 firewire_ohci
sdhci                  33205  1 sdhci_pci
crc_itu_t              12707  1 firewire_core
mark@marks-laptop:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        F0:4D:A2:57:DF:3F

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.187
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


- Device: eth2 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        78:E4:00:E2:99:02

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Cablesurf_338d46:Infra, 00:18:F3:E6:12:F9, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA
    BTVOYAGER2110-0C:Infra, 00:24:D2:80:2E:0C, Freq 2417 MHz, Rate 54 Mb/s, Strength 27 WEP
    eircom4166 6254: Infra, 00:0F:CC:87:63:60, Freq 2442 MHz, Rate 0 Mb/s, Strength 19 WEP
    eircom1646 6424: Infra, 00:0F:CC:3A:62:D8, Freq 2442 MHz, Rate 0 Mb/s, Strength 19 WEP


mark@marks-laptop:~$ sudo iwlist scan
[sudo] password for mark: 
lo        Interface doesn't support scanning.

eth2      Scan completed :
          Cell 01 - Address: 00:24:D2:80:2E:0C
                    ESSID:"BTVOYAGER2110-0C"
                    Mode:Managed
                    Frequency:2.417 GHz (Channel 2)
                    Quality:1/5  Signal level:-82 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 02 - Address: 00:18:F3:E6:12:F9
                    ESSID:"Cablesurf_338d46"
                    Mode:Managed
                    Frequency=2.412 GHz (Channel 1)
                    Quality:2/5  Signal level:-73 dBm  Noise level:-92 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 03 - Address: 00:0F:CC:87:63:60
                    ESSID:"eircom4166 6254"
                    Mode:Managed
                    Frequency:2.442 GHz (Channel 7)
                    Quality:1/5  Signal level:-86 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s

eth0      Interface doesn't support scanning.


```

```
mark@marks-laptop:~$ sudo cat /var/log/syslog | grep -e wl -e firmware -e eth1 -e wpa -e etork | tail -n55
Apr 23 13:47:06 marks-laptop NetworkManager[827]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:04:00.0/ssb0:0/net/wlan0, iface: wlan0)
Apr 23 13:47:06 marks-laptop NetworkManager[827]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:04:00.0/ssb0:0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Apr 23 13:47:06 marks-laptop NetworkManager[827]: <info> monitoring kernel firmware directory '/lib/firmware'.
Apr 23 13:47:06 marks-laptop NetworkManager[827]: <info> (wlan0): using nl80211 for WiFi device control
Apr 23 13:47:06 marks-laptop NetworkManager[827]: <warn> (wlan0): driver supports Access Point (AP) mode
Apr 23 13:47:06 marks-laptop NetworkManager[827]: <info> (wlan0): new 802.11 WiFi device (driver: 'b43' ifindex: 3)
Apr 23 13:47:06 marks-laptop NetworkManager[827]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Apr 23 13:47:06 marks-laptop NetworkManager[827]: <info> (wlan0): now managed
Apr 23 13:47:06 marks-laptop NetworkManager[827]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Apr 23 13:47:06 marks-laptop NetworkManager[827]: <info> (wlan0): bringing up device.
Apr 23 13:47:06 marks-laptop NetworkManager[827]: <info> (wlan0): deactivating device (reason 'managed') [2]
Apr 23 13:47:06 marks-laptop kernel: [   20.450932] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr 23 13:55:48 marks-laptop NetworkManager[827]: <info> (wlan0): now unmanaged
Apr 23 13:55:48 marks-laptop NetworkManager[827]: <info> (wlan0): device state change: unavailable -> unmanaged (reason 'sleeping') [20 10 37]
Apr 23 14:00:45 marks-laptop NetworkManager[827]: <info> (wlan0): now managed
Apr 23 14:00:45 marks-laptop NetworkManager[827]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Apr 23 14:00:45 marks-laptop NetworkManager[827]: <info> (wlan0): bringing up device.
Apr 23 14:00:45 marks-laptop NetworkManager[827]: <info> (wlan0): deactivating device (reason 'managed') [2]
Apr 23 16:05:32 marks-laptop NetworkManager[827]: <info> (wlan0): now unmanaged
Apr 23 16:05:32 marks-laptop NetworkManager[827]: <info> (wlan0): device state change: unavailable -> unmanaged (reason 'sleeping') [20 10 37]
Apr 23 16:14:50 marks-laptop NetworkManager[827]: <info> (wlan0): now managed
Apr 23 16:14:50 marks-laptop NetworkManager[827]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Apr 23 16:14:50 marks-laptop NetworkManager[827]: <info> (wlan0): bringing up device.
Apr 23 16:14:50 marks-laptop NetworkManager[827]: <info> (wlan0): deactivating device (reason 'managed') [2]
Apr 23 16:32:27 marks-laptop NetworkManager[827]: <info> (wlan0): now unmanaged
Apr 23 16:32:27 marks-laptop NetworkManager[827]: <info> (wlan0): device state change: unavailable -> unmanaged (reason 'sleeping') [20 10 37]
Apr 23 16:59:48 marks-laptop NetworkManager[827]: <info> (wlan0): now managed
Apr 23 16:59:48 marks-laptop NetworkManager[827]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Apr 23 16:59:48 marks-laptop NetworkManager[827]: <info> (wlan0): bringing up device.
Apr 23 16:59:48 marks-laptop NetworkManager[827]: <info> (wlan0): deactivating device (reason 'managed') [2]
Apr 23 17:08:24 marks-laptop kernel: [   17.930561] wl: module license 'MIXED/Proprietary' taints kernel.
Apr 23 17:08:24 marks-laptop kernel: [   17.936992] wl 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Apr 23 17:08:24 marks-laptop kernel: [   17.937089] wl 0000:04:00.0: setting latency timer to 64
Apr 23 17:08:24 marks-laptop kernel: [   18.265110] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 5.100.82.38
Apr 23 17:08:24 marks-laptop NetworkManager[829]: <info> monitoring kernel firmware directory '/lib/firmware'.
Apr 23 17:08:24 marks-laptop NetworkManager[829]: <info> (eth2): new 802.11 WiFi device (driver: 'wl' ifindex: 3)
Apr 23 17:08:46 marks-laptop dbus[811]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Apr 23 17:08:46 marks-laptop dbus[811]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Apr 23 17:08:46 marks-laptop NetworkManager[829]: <info> wpa_supplicant started
Apr 23 17:08:46 marks-laptop wpa_supplicant[1843]: nl80211: 'nl80211' generic netlink not found

```

---

### Post by wildmanne39 on 2012-04-23
Hi, it found networks just not yours.

That is the reason I switched drivers in the first place.

Change your encryption to none and reset your router then delete your wireless connection you set up and reboot then let network manager find your network.

I have to go out for a little while post the output of:
```
nm-tool
sudo iwlist scan
```
after you do the above.
Thanks

---

### Post by markaokeeffe on 2012-04-23
Okay I think we have made a giant leap! The internet is working perfectly at the moment, is it because there is no encryption on the router? Here is the output of that:```
mark@marks-laptop:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        F0:4D:A2:57:DF:3F

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         off


- Device: eth2  [dlink] --------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        78:E4:00:E2:99:02

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Cablesurf_338d46:Infra, 00:18:F3:E6:12:F9, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA
    vodafoneSecure_218C: Infra, 06:0C:C3:54:21:8C, Freq 2462 MHz, Rate 0 Mb/s, Strength 20 WPA WPA2
    eircom4166 6254: Infra, 00:0F:CC:87:63:60, Freq 2442 MHz, Rate 54 Mb/s, Strength 32 WEP
    BTVOYAGER2110-0C:Infra, 00:24:D2:80:2E:0C, Freq 2417 MHz, Rate 54 Mb/s, Strength 30 WEP
    vodafone_218C:   Infra, 00:0C:C3:54:21:8C, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WEP
    *dlink:          Infra, 00:21:91:EC:BC:FE, Freq 2452 MHz, Rate 54 Mb/s, Strength 100

  IPv4 Settings:
    Address:         192.168.0.198
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


mark@marks-laptop:~$ sudo iwlist scan
[sudo] password for mark: 
lo        Interface doesn't support scanning.

eth2      Scan completed :
          Cell 01 - Address: 00:21:91:EC:BC:FE
                    ESSID:"dlink"
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:5/5  Signal level:-49 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:24:D2:80:2E:0C
                    ESSID:"BTVOYAGER2110-0C"
                    Mode:Managed
                    Frequency:2.417 GHz (Channel 2)
                    Quality:2/5  Signal level:-79 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 03 - Address: 00:18:F3:E6:12:F9
                    ESSID:"Cablesurf_338d46"
                    Mode:Managed
                    Frequency=2.412 GHz (Channel 1)
                    Quality:4/5  Signal level:-67 dBm  Noise level:-92 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 04 - Address: 00:0F:CC:87:63:60
                    ESSID:"eircom4166 6254"
                    Mode:Managed
                    Frequency:2.442 GHz (Channel 7)
                    Quality:1/5  Signal level:-83 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s

eth0      Interface doesn't support scanning.

```

---

### Post by wildmanne39 on 2012-04-23
Hi, now set your wireless encryption to just wpa2 not wpa/wpa2 if possible in your router and in network manager set it to wpa/wpa2 personal unless you have just wpa2 personal option then use it.
Thanks

---

### Post by markaokeeffe on 2012-04-23
Solved! Thank you so much, you've been a great help!

---

### Post by wildmanne39 on 2012-04-23
Hi, your welcome! 
Enjoy

---

### Post by jmontgom10 on 2013-02-16
Hi Wild Man,

I know this is an older post, but after a recent update I seem to be having similar problems to what markaokeeffe had. I can connect to other wireless routers at work, but the D-link router in my home is giving me problems. I have set my router to WPA2 only mode and changed my network manager to WPA2 mode, too, but that does not seem to be solving the problem.

Any insight you are willing to offer would be deeply appreciated.

Here is the output from some potentially helpful commands.

```

# cat /etc/lsb-release; uname -a

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"
Linux ubuntu 3.5.0-23-generic #35~precise1-Ubuntu SMP Fri Jan 25 17:15:33 UTC 2013 i686 i686 i386 GNU/Linux

```

```

# lspci -nnk | grep -iA2 net

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Toshiba America Info Systems Device [1179:fd30]
	Kernel driver in use: r8169
--
07:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
	Subsystem: Askey Computer Corp. Device [144f:7175]
	Kernel driver in use: wl

```

```

# lsusb

Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:5801 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 0930:0214 Toshiba Corp. 
Bus 002 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 004: ID 0000:0000  

```

```

# iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

```

# rfkill list all

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

```

# lsmod

Module                  Size  Used by
nls_iso8859_1          12618  1 
dm_crypt               22572  0 
lib80211_crypt_tkip    17276  0 
btusb                  17952  0 
wl                   2906598  0 
coretemp               13362  0 
kvm_intel             127736  0 
kvm                   365556  1 kvm_intel
aesni_intel            17979  0 
cryptd                 19822  1 aesni_intel
aes_i586               16996  1 aesni_intel
snd_hda_codec_hdmi     31778  1 
snd_hda_codec_realtek    64876  1 
snd_hda_intel          33029  3 
snd_hda_codec         116477  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13277  1 snd_hda_codec
snd_pcm                81124  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
joydev                 17394  0 
uvcvideo               72249  0 
videobuf2_core         32212  1 uvcvideo
videodev              100265  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12757  1 uvcvideo
videobuf2_memops       13213  1 videobuf2_vmalloc
snd_seq_midi           13133  0 
microcode              18396  0 
snd_rawmidi            25426  1 snd_seq_midi
snd_seq_midi_event     14476  1 snd_seq_midi
cfg80211              181041  1 wl
snd_seq                51594  2 snd_seq_midi,snd_seq_midi_event
psmouse                91022  0 
serio_raw              13032  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
lib80211               14041  2 lib80211_crypt_tkip,wl
intel_ips              17956  0 
lpc_ich                16993  0 
jmb38x_ms              17407  0 
snd                    62675  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
memstick               15886  1 jmb38x_ms
mei                    36404  0 
soundcore              14636  1 snd
snd_page_alloc         14109  2 snd_hda_intel,snd_pcm
toshiba_acpi           18287  0 
sparse_keymap          13659  1 toshiba_acpi
wmi                    18745  1 toshiba_acpi
bnep                   17791  2 
parport_pc             32115  0 
rfcomm                 38104  12 
bluetooth             189585  24 btusb,bnep,rfcomm
ppdev                  12850  0 
toshiba_bluetooth      12712  0 
binfmt_misc            17293  1 
mac_hid                13078  0 
lp                     17456  0 
parport                40931  3 parport_pc,ppdev,lp
uas                    17745  0 
usb_storage            39720  1 
hid_logitech_dj        18312  0 
usbhid                 46054  1 hid_logitech_dj
hid                    82511  2 hid_logitech_dj,usbhid
i915                  470823  8 
r8169                  56853  0 
drm_kms_helper         47459  1 i915
sdhci_pci              18263  0 
sdhci                  32293  1 sdhci_pci
drm                   240232  4 i915,drm_kms_helper
i2c_algo_bit           13317  1 i915
video                  19070  1 i915

```

---

