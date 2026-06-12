---
title: "Can't connect to wireless networks"
date: 2012-03-25
forum: Networking &amp; Wireless
---

### Post by tillhg on 2012-03-25
Hi everyone,
i just got a new wireless LAN USB adapter. When it's plugged Ubuntu shows all the available wireless networks in my area but I can't connect to one of them. After choosing a network and typing the password Ubuntu tries to connect to the network but after a few seconds there is a message that I'm disconnected.
A test with Windows proves that it is actually possible to connect to the network.
I haven't installed any driver because I don't know which one I should install.
Here are my "iwconfig" and "lspci" information:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
wlan1     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
```
(wlan1 is the wireless card I'm speaking about.)

```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GT216 [GeForce GT 240M] (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
03:00.0 Network controller: Intel Corporation WiFi Link 5100
```

I hope you can help me solve this problem!

(I have Ubuntu 11.10)

---

### Post by wildmanne39 on 2012-03-25
Hi, first you have an internal card do you not want to get it to work?

Please post the output of these commands:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
rfkill list all
lsmod
```
Thanks

---

### Post by tillhg on 2012-03-27
I thought my internal card already works. It just don't have a range as good as my usb-wireless-card's one.

Here are the outputs you asked for:
```

till@till-Aspire-8735:/$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux till-Aspire-8735 3.0.0-16-generic #29-Ubuntu SMP Tue Feb 14 12:48:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
till@till-Aspire-8735:/$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)
	Subsystem: Acer Incorporated [ALI] Device [1025:0207]
	Kernel driver in use: tg3
--
03:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]
	Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1201]
	Kernel driver in use: iwlagn
till@till-Aspire-8735:/$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN
Bus 002 Device 004: ID 04f2:b044 Chicony Electronics Co., Ltd Acer CrystalEye Webcam
Bus 005 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
till@till-Aspire-8735:/$ rfkill list all
0: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: no
till@till-Aspire-8735:/$ lsmod
Module                  Size  Used by
parport_pc             36962  0 
ppdev                  17113  0 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
joydev                 17693  0 
snd_hda_codec_hdmi     32040  4 
arc4                   12529  4 
rtl8192cu             103210  0 
rtl8192c_common        75767  1 rtl8192cu
rtlwifi               110972  1 rtl8192cu
acer_wmi               23948  0 
sparse_keymap          13890  1 acer_wmi
snd_hda_codec_realtek   330815  1 
binfmt_misc            17540  1 
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_hda_intel          33390  3 
snd_hda_codec         104931  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
iwlagn                314257  0 
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
mac80211              462046  4 rtl8192cu,rtl8192c_common,rtlwifi,iwlagn
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
psmouse                73882  0 
snd_seq_midi_event     14899  1 snd_seq_midi
cfg80211              199630  3 rtlwifi,iwlagn,mac80211
serio_raw              13166  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
nouveau               728677  4 
ttm                    76805  1 nouveau
drm_kms_helper         42558  1 nouveau
drm                   236290  6 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13423  1 nouveau
mxm_wmi                12979  1 nouveau
snd                    68266  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  19412  1 nouveau
soundcore              12680  1 snd
wmi                    19256  2 acer_wmi,mxm_wmi
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
ahci                   26002  2 
libahci                26861  1 ahci
tg3                   147729  0 

```

---

### Post by wildmanne39 on 2012-03-27
Hi, ubuntu installed the driver for you it is already there, try this please:
```
sudo rmmod -f iwlagn
sudo modprobe rtl8192cu
```
give it a few seconds to come on, if it does not check and make sure wireless is enabled in the network icon in the top right corner of the screen, then if it still does not work reboot and run these commands please and post the output here:
```
nm-tool
sudo iwlist scan
```
```
sudo cat /var/log/syslog | grep -e rtl -e firmware -e wpa -e wlan -e etork | tail -n55
```
Thanks

---

### Post by tillhg on 2012-03-30
Sorry for the late reply..

I did everything you said but it still doesn't work. I don't know what to do now...
However thank you so much for trying to help me!

---

### Post by wildmanne39 on 2012-03-30
Hi, the commands that I asked you to run after you rebooted please post the output here so we can have a look at it. Place the information between the code tags by clicking on #.
Thanks

---

### Post by tillhg on 2012-03-31
Okay, here are the outputs. I switched to Ubuntu 12.04 LTS Beta since my last post. I hope this doesn't change anything. Anyway, my problems with the wireless card are exactly the same as before.

```
till@till-Aspire-8735:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan1 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             disconnected
  Default:           no
  HW Address:        00:E0:4C:0A:F2:72

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    wiGi-Repeat:     Infra, 00:23:13:09:8D:B6, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2
    Evolette_Lashana:Infra, 1C:BD:B9:8F:FD:DC, Freq 2437 MHz, Rate 54 Mb/s, Strength 99 WPA WPA2
    PS3-3937333:     Infra, 00:1E:4C:AF:F0:60, Freq 2437 MHz, Rate 54 Mb/s, Strength 99 WPA
    ALICE-WLAN10:    Infra, 00:D0:DE:84:FD:C7, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA
    TillNetwork:     Infra, 00:26:5A:B1:65:54, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             disconnected
  Default:           no
  HW Address:        00:1E:65:9A:56:66

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Evolette_Lashana:Infra, 1C:BD:B9:8F:FD:DC, Freq 2437 MHz, Rate 54 Mb/s, Strength 80 WPA WPA2
    wiGi-Repeat:     Infra, 00:23:13:09:8D:B6, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WPA2
    PS3-3937333:     Infra, 00:1E:4C:AF:F0:60, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA
    ALICE-WLAN10:    Infra, 00:D0:DE:84:FD:C7, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA
    FRITZ!Box WLAN 3270: Infra, BC:05:43:19:38:41, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA2
    Furkan:          Infra, 14:D6:4D:E6:E3:7E, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA2
    TillNetwork:     Infra, 00:26:5A:B1:65:54, Freq 2437 MHz, Rate 54 Mb/s, Strength 58 WEP


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        00:1F:16:C6:ED:C9

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.109
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

```
```
till@till-Aspire-8735:~$ sudo iwlist scan
[sudo] password for till: 
lo        Interface doesn't support scanning.

wlan1     No scan results

wlan0     Scan completed :
          Cell 01 - Address: 00:26:5A:B1:65:54
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"TillNetwork"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000045c55db045
                    Extra: Last beacon: 2564ms ago
                    IE: Unknown: 000B54696C6C4E6574776F726B
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1606070500000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706474220010D10
                    IE: Unknown: DD1E00904C33EE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3406070500000000000000000000000000000000000000
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD750050F204104A00011010440001021041000100103B000103104700104517365BE5911D8490B800265AB1655410210006442D4C696E6B102300074449522D363135102400074449522D3631351042000830303030303030301054000800060050F2040001101100074449522D363135100800020086
          Cell 02 - Address: BC:05:43:19:38:41
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box WLAN 3270"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000022ecf91183
                    Extra: Last beacon: 12612ms ago
                    IE: Unknown: 0013465249545A21426F7820574C414E2033323730
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1ACE131BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D16010D0A00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010020000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 03 - Address: 00:1E:4C:AF:F0:60
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"PS3-3937333"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000199f51790c4
                    Extra: Last beacon: 2568ms ago
                    IE: Unknown: 000B5053332D33393337333333
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 0406000200000000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
          Cell 04 - Address: 1C:BD:B9:8F:FD:DC
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"Evolette_Lashana"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000244cbef8173
                    Extra: Last beacon: 2532ms ago
                    IE: Unknown: 001045766F6C657474655F4C617368616E61
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1606070700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706474220010D10
                    IE: Unknown: DD1E00904C33EE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3406070700000000000000000000000000000000000000
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD750050F204104A00011010440001011041000100103B00010310470010FF2ACEFFE537E96097F71CBDB98FFDDC10210006442D4C696E6B102300074449522D363135102400074449522D3631351042000830303030303030301054000800060050F2040001101100074449522D363135100800020086
          Cell 05 - Address: 00:23:13:09:8D:B6
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"wiGi-Repeat"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000015c5ed179
                    Extra: Last beacon: 2544ms ago
                    IE: Unknown: 000B776947692D526570656174
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0600E04C020160
          Cell 06 - Address: 14:D6:4D:E6:E3:7E
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"Furkan"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002b5334d416c
                    Extra: Last beacon: 2548ms ago
                    IE: Unknown: 00064675726B616E
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD130050F204104A00011010440001021041000100
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1AEC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1606000000000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000006127A
                    IE: Unknown: DD1E00904C33EC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3406000000000000000000000000000000000000000000
                    IE: Unknown: DD07000C4307000000

eth0      Interface doesn't support scanning.
```
```
till@till-Aspire-8735:~$ sudo cat /var/log/syslog | grep -e rtl -e firmware -e wpa -e wlan -e etork | tail -n55
Mar 31 10:44:28 till-Aspire-8735 wpa_supplicant[933]: CTRL-EVENT-CONNECTED - Connection to 00:26:5a:b1:65:54 completed (auth) [id=0 id_str=]
Mar 31 10:44:28 till-Aspire-8735 kernel: [   82.890262] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
Mar 31 10:44:28 till-Aspire-8735 NetworkManager[784]: <info> (wlan1): supplicant interface state: associating -> completed
Mar 31 10:44:28 till-Aspire-8735 NetworkManager[784]: <info> Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'TillNetwork'.
Mar 31 10:44:28 till-Aspire-8735 NetworkManager[784]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) scheduled.
Mar 31 10:44:28 till-Aspire-8735 NetworkManager[784]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) started...
Mar 31 10:44:28 till-Aspire-8735 NetworkManager[784]: <info> (wlan1): device state change: config -> ip-config (reason 'none') [50 70 0]
Mar 31 10:44:28 till-Aspire-8735 NetworkManager[784]: <info> Activation (wlan1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Mar 31 10:44:28 till-Aspire-8735 NetworkManager[784]: <info> Activation (wlan1) Beginning IP6 addrconf.
Mar 31 10:44:28 till-Aspire-8735 NetworkManager[784]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) complete.
Mar 31 10:44:28 till-Aspire-8735 NetworkManager[784]: <info> (wlan1): DHCPv4 state changed nbi -> preinit
Mar 31 10:44:28 till-Aspire-8735 dhclient: Listening on LPF/wlan1/00:e0:4c:0a:f2:72
Mar 31 10:44:28 till-Aspire-8735 dhclient: Sending on   LPF/wlan1/00:e0:4c:0a:f2:72
Mar 31 10:44:28 till-Aspire-8735 dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 3
Mar 31 10:44:29 till-Aspire-8735 avahi-daemon[779]: Joining mDNS multicast group on interface wlan1.IPv6 with address fe80::2e0:4cff:fe0a:f272.
Mar 31 10:44:29 till-Aspire-8735 avahi-daemon[779]: New relevant interface wlan1.IPv6 for mDNS.
Mar 31 10:44:29 till-Aspire-8735 avahi-daemon[779]: Registering new address record for fe80::2e0:4cff:fe0a:f272 on wlan1.*.
Mar 31 10:44:31 till-Aspire-8735 dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 8
Mar 31 10:44:38 till-Aspire-8735 kernel: [   93.008067] wlan1: no IPv6 routers present
Mar 31 10:44:39 till-Aspire-8735 dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 8
Mar 31 10:44:47 till-Aspire-8735 dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 9
Mar 31 10:44:48 till-Aspire-8735 NetworkManager[784]: <info> (wlan1): IP6 addrconf timed out or failed.
Mar 31 10:44:48 till-Aspire-8735 NetworkManager[784]: <info> Activation (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Mar 31 10:44:48 till-Aspire-8735 NetworkManager[784]: <info> Activation (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) started...
Mar 31 10:44:48 till-Aspire-8735 NetworkManager[784]: <info> Activation (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Mar 31 10:44:56 till-Aspire-8735 dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 10
Mar 31 10:45:01 till-Aspire-8735 NetworkManager[784]: <info> (wlan0): device state change: activated -> disconnected (reason 'user-requested') [100 30 39]
Mar 31 10:45:02 till-Aspire-8735 NetworkManager[784]: <info> (wlan0): deactivating device (reason 'user-requested') [39]
Mar 31 10:45:02 till-Aspire-8735 NetworkManager[784]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1674
Mar 31 10:45:02 till-Aspire-8735 avahi-daemon[779]: Withdrawing address record for fe80::21e:65ff:fe9a:5666 on wlan0.
Mar 31 10:45:02 till-Aspire-8735 avahi-daemon[779]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::21e:65ff:fe9a:5666.
Mar 31 10:45:02 till-Aspire-8735 avahi-daemon[779]: Interface wlan0.IPv6 no longer relevant for mDNS.
Mar 31 10:45:02 till-Aspire-8735 avahi-daemon[779]: Withdrawing address record for 192.168.0.102 on wlan0.
Mar 31 10:45:02 till-Aspire-8735 avahi-daemon[779]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.102.
Mar 31 10:45:02 till-Aspire-8735 NetworkManager[784]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Mar 31 10:45:02 till-Aspire-8735 kernel: [  116.594877] wlan0: deauthenticating from 00:26:5a:b1:65:54 by local choice (reason=3)
Mar 31 10:45:02 till-Aspire-8735 avahi-daemon[779]: Interface wlan0.IPv4 no longer relevant for mDNS.
Mar 31 10:45:02 till-Aspire-8735 wpa_supplicant[933]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=3
Mar 31 10:45:02 till-Aspire-8735 NetworkManager[784]: <info> (wlan0): supplicant interface state: completed -> disconnected
Mar 31 10:45:03 till-Aspire-8735 avahi-daemon[779]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::21e:65ff:fe9a:5666.
Mar 31 10:45:03 till-Aspire-8735 avahi-daemon[779]: New relevant interface wlan0.IPv6 for mDNS.
Mar 31 10:45:03 till-Aspire-8735 avahi-daemon[779]: Registering new address record for fe80::21e:65ff:fe9a:5666 on wlan0.*.
Mar 31 10:45:06 till-Aspire-8735 dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 11
Mar 31 10:45:08 till-Aspire-8735 NetworkManager[784]: <info> (wlan1): device state change: ip-config -> disconnected (reason 'user-requested') [70 30 39]
Mar 31 10:45:08 till-Aspire-8735 NetworkManager[784]: <info> (wlan1): deactivating device (reason 'user-requested') [39]
Mar 31 10:45:08 till-Aspire-8735 NetworkManager[784]: <info> (wlan1): canceled DHCP transaction, DHCP client pid 2407
Mar 31 10:45:08 till-Aspire-8735 avahi-daemon[779]: Withdrawing address record for fe80::2e0:4cff:fe0a:f272 on wlan1.
Mar 31 10:45:08 till-Aspire-8735 avahi-daemon[779]: Leaving mDNS multicast group on interface wlan1.IPv6 with address fe80::2e0:4cff:fe0a:f272.
Mar 31 10:45:08 till-Aspire-8735 avahi-daemon[779]: Interface wlan1.IPv6 no longer relevant for mDNS.
Mar 31 10:45:08 till-Aspire-8735 kernel: [  122.622944] wlan1: deauthenticating from 00:26:5a:b1:65:54 by local choice (reason=3)
Mar 31 10:45:08 till-Aspire-8735 wpa_supplicant[933]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=3
Mar 31 10:45:08 till-Aspire-8735 NetworkManager[784]: <info> (wlan1): supplicant interface state: completed -> disconnected
Mar 31 10:45:09 till-Aspire-8735 avahi-daemon[779]: Joining mDNS multicast group on interface wlan1.IPv6 with address fe80::2e0:4cff:fe0a:f272.
Mar 31 10:45:09 till-Aspire-8735 avahi-daemon[779]: New relevant interface wlan1.IPv6 for mDNS.
Mar 31 10:45:09 till-Aspire-8735 avahi-daemon[779]: Registering new address record for fe80::2e0:4cff:fe0a:f272 on wlan1.*.
```

---

### Post by wildmanne39 on 2012-03-31
Hi, TillNetwork is the network you want to connect to right?

We will probably need to disable the internal card to use the usb card.

Set IPV6 to ignore like in the screenshot
then run:
```
sudo rmmod -f iwlagn
sudo modprobe rtl8192cu
```
do not reboot and give it a few seconds to come on with the usb device plugged in does it activate?

If not post the output of:
```
lsmod | grep 819
```
Thanks

---

### Post by tillhg on 2012-03-31
Yes, TillNetwork is the network I want to connect to.
After setting TillNetwork to be ignored I typed the commands you wrote but the output of the first one was
```
ERROR: Removing 'iwlagn': No such file or directory
```
and the other two commands didn't output anything.

---

### Post by wildmanne39 on 2012-03-31
Hi, please post the output of: 
```
lsmod
```
Thanks

---

### Post by tillhg on 2012-03-31
Here it is:
```
Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39553  1 
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
joydev                 17393  0 
snd_hda_codec_hdmi     31775  4 
arc4                   12473  4 
snd_hda_codec_realtek   174055  1 
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
snd_hda_intel          32765  5 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
acer_wmi               23612  0 
snd_seq_midi_event     14475  1 snd_seq_midi
mxm_wmi                12859  0 
binfmt_misc            17292  1 
sparse_keymap          13658  1 acer_wmi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
nvidia              10933002  53 
iwlwifi               291847  0 
rtl8192cu              97722  0 
rtl8192c_common        69519  1 rtl8192cu
psmouse                72846  0 
uvcvideo               67203  0 
rtlwifi                95804  1 rtl8192cu
serio_raw              13027  0 
videodev               86588  1 uvcvideo
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              436455  4 rtl8192cu,rtl8192c_common,iwlwifi,rtlwifi
cfg80211              178679  3 iwlwifi,rtlwifi,mac80211
snd                    62064  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    18744  2 acer_wmi,mxm_wmi
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
mac_hid                13077  0 
video                  18907  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41906  0 
hid                    77367  1 usbhid
tg3                   141369  0 
```

---

### Post by wildmanne39 on 2012-03-31
Hi, there is a bug that prevents it from working it always has to be compiled from realtek come to find out but since you are using 12.04 now they do not have a driver for it yet.
Thanks

---

### Post by tillhg on 2012-04-01
So what do you suggest me to do? Switching back to Ubuntu 11.10?

---

### Post by wildmanne39 on 2012-04-01
Hi, you can do that or wait for realtek to get a driver for 12.04 out, they are usually pretty quick about it.
Thanks

---

### Post by tillhg on 2012-04-03
Okay, thank you very much for your help! I will wait for realtek to get the driver out.

---

### Post by wildmanne39 on 2012-04-03
Hi, your welcome!

---

### Post by tillhg on 2012-06-20
Hi, sorry that I post something after such a long time but my wireless card still does not work. I said I would walk for Realtek to get the driver out but now the release of Ubuntu 12.04 is two month ago. Is there really no chance to get this fixed?
Thanks in advance.

---

