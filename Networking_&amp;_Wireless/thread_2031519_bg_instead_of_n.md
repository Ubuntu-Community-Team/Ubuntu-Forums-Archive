---
title: "b/g instead of n?"
date: 2012-07-22
forum: Networking &amp; Wireless
---

### Post by icegood on 2012-07-22
Under kubuntu i have connection:
```

Type: Wireless 802.11
Connection State: Connected
IP Address: 192.168.73.177
Connection Speed: 19.5 MBit/s
System Name: wlan0
MAC Address: 1C:4B:D6:D5:81:EC
Driver: ath9k
Access Point (SSID): ice dd-wrt
Access Point (MAC): BC:F6:85:43:18:02
Band: b/g
Channel: 13 (2472 MHz)

```

Why n mode doesn't created? Where should i update config files?
In windows 7 from same machine everything is OK. So, in particular, router is OK too.

---

### Post by praseodym on 2012-07-22
Maybe a driver bug?! Please show

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
sudo iwlist scan
```

---

### Post by icegood on 2012-07-22
> **praseodym said:**
> Maybe a driver bug?! Please show
...
lspci -nnk | grep -iA2 net:
```

04:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: AzureWave AW-NE785 / AW-NE785H 802.11bgn Wireless Full or Half-size Mini PCIe Card [1a3b:1089]
    Kernel driver in use: ath9k
--
05:00.5 Ethernet controller [0200]: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller [197b:0250] (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1905]
    Kernel driver in use: jme

```
lsusb:
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b1e5 Chicony Electronics Co., Ltd 

```
lsmod:
```

Module                  Size  Used by
bnep                   18281  2 
rfcomm                 47604  0 
parport_pc             32866  0 
ppdev                  17113  0 
bluetooth             180104  10 bnep,rfcomm
joydev                 17693  0 
snd_hda_codec_hdmi     32474  1 
sp5100_tco             13791  0 
snd_hda_codec_realtek   223867  1 
edac_core              53746  0 
edac_mce_amd           23709  0 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
i2c_piix4              13301  0 
v4l2_compat_ioctl32    17128  1 videodev
psmouse                87692  0 
serio_raw              13211  0 
arc4                   12529  2 
k10temp                13166  0 
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
ath9k                 132390  0 
snd                    78855  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              506816  1 ath9k
ath9k_common           14053  1 ath9k
ath9k_hw              411112  2 ath9k,ath9k_common
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
jmb38x_ms              17646  0 
cfg80211              205544  3 ath9k,mac80211,ath
memstick               16569  1 jmb38x_ms
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mac_hid                13253  0 
asus_laptop            24493  0 
sparse_keymap          13890  1 asus_laptop
input_polldev          13896  1 asus_laptop
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
video                  19596  0 
radeon                804372  3 
ttm                    76949  1 radeon
drm_kms_helper         46978  1 radeon
drm                   242038  5 radeon,ttm,drm_kms_helper
jme                    41259  0 
i2c_algo_bit           13423  1 radeon
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci

```
iwconfig:
```

wlan0     IEEE 802.11bgn  ESSID:"ice dd-wrt"  
          Mode:Managed  Frequency:2.472 GHz  Access Point: BC:F6:85:43:18:02   
          Bit Rate=58.5 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=30/70  Signal level=-80 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
 iwlist scan:
```

wlan0     Scan completed :
          Cell 01 - Address: BC:F6:85:43:18:02
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"ice dd-wrt"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000025524c164
                    Extra: Last beacon: 40ms ago
                    IE: Unknown: 000A6963652064642D777274
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010D
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D160D000000000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000005127A
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706444520010D10
          Cell 02 - Address: 90:F6:52:66:B4:C4
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"ROMAN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001340d6cd80
                    Extra: Last beacon: 132ms ago
                    IE: Unknown: 0005524F4D414E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B071B00000000000000000000000000000000000000
                    IE: Unknown: 3D160B071B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000
                    IE: Unknown: DD850050F204104A0001101044000101103B000103104700100000000000001000000090F65266B4C41021000754502D4C494E4B10230009544C2D57523734314E10240007312E302F322E3010420003312E301054000800060050F204000110110019576972656C65737320526F7574657220544C2D57523734314E100800020086103C000101
          Cell 03 - Address: D8:5D:4C:A4:01:D6
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"RouterWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002fcfc22181
                    Extra: Last beacon: 216ms ago
                    IE: Unknown: 000A526F7574657257694669
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
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

```

---

### Post by praseodym on 2012-07-22
It is some kind of bug. Deactivate the hardware encryption of the driver ath9k:

> echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k

---

### Post by icegood on 2012-07-23
Seems everything is much simpler than looks. From my last status:
```

Type: Wireless 802.11
Connection State: Connected
IP Address: 192.168.73.177
Connection Speed: 108 MBit/s
System Name: wlan0
MAC Address: 1C:4B:D6:D5:81:EC
Driver: ath9k
Access Point (SSID): ice dd-wrt
Access Point (MAC): BC:F6:85:43:18:02
Band: b/g
Channel: 13 (2472 MHz)

```

108 MBit/s is out of b/g mode but still b/g mode shown. It seems that mode itself wrongly shown.
I'm also expirienced an one [known]("https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/1006141") error in log:
```

Jul 23 07:56:59 ubuntu NetworkManager[985]: <error> [1343019419.920548] [wifi-utils-nl80211.c:654] nl80211_wiphy_info_handler(): Don't know the meaning of NL80211_ATTR_CIPHER_SUITES 0x000fac06.
Jul 23 07:56:59 ubuntu NetworkManager[985]: <error> [1343019419.973614] [nm-device-ethernet.c:456] real_update_permanent_hw_address(): (eth0): unable to read permanent MAC address (error 0)

```
Maybe because of this KDE applet goes mad.

---

