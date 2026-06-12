---
title: "Dell Latitude D610 - WiFi setup"
date: 2012-11-17
forum: Networking &amp; Wireless
---

### Post by qwikrazor87 on 2012-11-17
Hello everyone.
This is the first distro I am trying, which is Xubuntu 12.10. I have it dual booting with Windows XP since I can't get the WiFi working on Xubuntu.
I tried following --> [this tutorial]("http://ubuntuforums.org/showthread.php?t=1604868") <-- but I am completely at loss of what I am doing, I need a way to get WiFi working without internet access on Xubuntu. I have access through WiFi on Windows XP from which I can download the necessary files.
I downloaded the files in solution #2 at that link but I had to get linux-headers packages for kernel 3.5.0.
I would really appreciate any and all help.
////
I forgot to mention that I have a Broadcom BCM4318 driver.

---

### Post by ahallubuntu on 2012-11-17
You might try the solution here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers)

and scroll down to the section titled "No internet access" .  Download the files suggested there while you are booted into XP, then in Xubuntu mount your XP partition and copy the downloaded files from there and try to follow the instructions.  Download the files suggested for 12.04 .  I don't know if they will work for 12.10 or not.  Unless you have a good reason to need 12.10, consider sticking with 12.04 anyway - it is an LTS version supported until 2017.  12.10 will be supported for only another 18 months, then you'll have to upgrade to get new updates.

FYI, on Dell laptops you generally have the option to replace your Broadcom wireless card with an Intel card (Dell sold the D610 with both), and the Intel card should work automatically.  Probably very easy to install and would cost all of about $10 USD.  Installing an Intel wireless card is almost always the first thing I do when I acquire laptop to refurbish.  I hate all the hassles of Broadcom wireless cards in Linux!

---

### Post by qwikrazor87 on 2012-11-17
Thank you very much for your help, I will download 12.04.

That does sound much easier getting an intel wireless card but for now I will download the other distro and try to get broadcom working on there.

That is the tutorial that I referred to in solution #2 in the link I posted but I might have better luck getting it working on 12.04. Thank you again.

---

### Post by wildmanne39 on 2012-11-17
Hi,

Download the b43 zip file to a flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
if you have not installed any other driver this should get your wireless working.
Thanks

---

### Post by qwikrazor87 on 2012-11-17
Hi Wild Man.
Thank you very much for your help. That solved my problem from my wireless card not showing up.
In the terminal I typed in iwconfig and now it shows up as this,
> iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID: off/any  
          Mode: Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit: 7   RTS thr: off   Fragment thr: off
          Power Management: off
          
eth0      no wireless extensions.After running the commands you told me to it said that wireless connection is now available.
My problem now is that I can't figure out how to setup up the wireless connection.
While in the network setup the wireless access point does not come up in the list.
Thanks.

---

### Post by wildmanne39 on 2012-11-17
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by qwikrazor87 on 2012-11-17
Hi Wild Man.
Thank you. Here are the results that I got.
```
qwikrazor87@qwikrazor87-Latitude-D610:~/Desktop$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
Linux qwikrazor87-Latitude-D610 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:04:05 UTC 2012 i686 i686 i386 GNU/Linux
qwikrazor87@qwikrazor87-Latitude-D610:~/Desktop$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)
    Subsystem: Dell Latitude D610 [1028:0182]
    Kernel driver in use: tg3
--
03:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
    Subsystem: Dell Wireless 1370 WLAN Mini-PCI Card [1028:0005]
    Kernel driver in use: b43-pci-bridge
qwikrazor87@qwikrazor87-Latitude-D610:~/Desktop$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
qwikrazor87@qwikrazor87-Latitude-D610:~/Desktop$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

qwikrazor87@qwikrazor87-Latitude-D610:~/Desktop$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
qwikrazor87@qwikrazor87-Latitude-D610:~/Desktop$ lsmod
Module                  Size  Used by
rfcomm                 38139  4 
joydev                 17393  0 
snd_intel8x0           33455  3 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80845  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
arc4                   12473  2 
pcmcia                 39791  0 
snd_seq_midi_event     14475  1 snd_seq_midi
dell_laptop            17767  0 
b43                   342643  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
dcdbas                 14098  1 dell_laptop
radeon                733687  2 
mac80211              436455  1 b43
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              178679  2 b43,mac80211
bnep                   17830  2 
psmouse                87213  0 
snd                    62064  13 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
serio_raw              13027  0 
bluetooth             158438  10 rfcomm,bnep
bcma                   25651  1 b43
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
ppdev                  12849  0 
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
parport_pc             32114  1 
drm                   197692  4 radeon,ttm,drm_kms_helper
mac_hid                13077  0 
video                  19068  0 
i2c_algo_bit           13199  1 radeon
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
ssb                    50691  1 b43
tg3                   137273  0
```

---

### Post by wildmanne39 on 2012-11-17
Hi, lets dig a little deeper, please post the results of:
```
nm-tool
sudo iwlist scan
cat /var/lib/NetworkManager/NetworkManager.state
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wlan -e wpa -e etork | tail -n55
```
Thanks

---

### Post by qwikrazor87 on 2012-11-17
Thank you for the quick responses. here are the results.
```
qwikrazor87@qwikrazor87-Latitude-D610:~/Desktop$ nm-tool

NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             disconnected
  Default:           no
  HW Address:        00:14:A5:36:21:86

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    GCI RBB:         Infra, F4:7F:35:74:7A:40, Freq 2462 MHz, Rate 54 Mb/s, Strength 74 WPA WPA2
    treat:           Infra, 22:4E:7F:47:6B:95, Freq 2422 MHz, Rate 54 Mb/s, Strength 52 WPA WPA2
    LKSDWireless:    Infra, 90:84:0D:DF:E7:35, Freq 2422 MHz, Rate 54 Mb/s, Strength 50
    LKSDWireless:    Infra, 00:19:E3:FA:34:88, Freq 2462 MHz, Rate 54 Mb/s, Strength 50
    GCI RBB:         Infra, 58:BF:EA:01:95:60, Freq 2412 MHz, Rate 54 Mb/s, Strength 82 WPA WPA2
    pepsi1:          Infra, 30:46:9A:00:2B:D4, Freq 2417 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    YKTELEMED:       Infra, 00:15:2B:21:D7:D2, Freq 2412 MHz, Rate 48 Mb/s, Strength 40 WEP
    YKDATA:          Infra, 00:15:2B:21:D7:D1, Freq 2412 MHz, Rate 48 Mb/s, Strength 40 WEP
    YKDATA:          Infra, 00:15:2B:21:C8:91, Freq 2412 MHz, Rate 48 Mb/s, Strength 25 WEP


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        00:12:3F:1F:7A:C9

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


qwikrazor87@qwikrazor87-Latitude-D610:~/Desktop$ sudo iwlist scan
[sudo] password for qwikrazor87: 
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 90:84:0D:DF:E7:35
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:off
                    ESSID:"LKSDWireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000d4c0a923fe
                    Extra: Last beacon: 1012ms ago
                    IE: Unknown: 000C4C4B5344576972656C657373
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030103
                    IE: Unknown: 050402030004
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0700039301720320
                    IE: Unknown: DD0E0017F2070001010690840DDFE735
          Cell 02 - Address: F4:7F:35:74:7A:40
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"GCI RBB"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000d4c0c9b5b9
                    Extra: Last beacon: 240ms ago
                    IE: Unknown: 000747434920524242
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B050500AA8D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D160B000500000000000000000000000000000000000000
                    IE: Unknown: 851E07008F000F00FF03590354756E756E616B5F41703200000000000500003E
                    IE: Unknown: 9606004096001900
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961401
          Cell 03 - Address: 00:19:E3:FA:34:88
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:off
                    ESSID:"LKSDWireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000004c93ee6
                    Extra: Last beacon: 480ms ago
                    IE: Unknown: 000C4C4B5344576972656C657373
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A0C501BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0700039301680320
                    IE: Unknown: DD0E0017F207000101060019E3FA3488
                    IE: Unknown: DD0B0017F20100010100000001
          Cell 04 - Address: 58:BF:EA:01:95:60
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"GCI RBB"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000d4c0739161
                    Extra: Last beacon: 1252ms ago
                    IE: Unknown: 000747434920524242
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B0509005E8D5B
                    IE: Unknown: 2A0102
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D1601000700000000000000000000000000000000000000
                    IE: Unknown: 851E0E008F000F00FF03590354756E756E616B5F41703100000000000900003E
                    IE: Unknown: 9606004096001900
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961401
          Cell 05 - Address: 00:15:2B:21:D7:D2
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"YKTELEMED"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000026e915b2192
                    Extra: Last beacon: 1236ms ago
                    IE: Unknown: 0009594B54454C454D4544
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 050400020000
                    IE: Unknown: 0B0400000200
                    IE: Unknown: 2A0102
                    IE: Unknown: 3203304860
                    IE: Unknown: 851E000084000F00FF031900544E4B2D313233312D3200000000000000000025
                    IE: Unknown: AD0F00A0F8000009000000640000000000
                    IE: Unknown: DD06004096010102
                    IE: Unknown: DD050040960303
                    IE: Unknown: DD1600409604000207A4000023A400004243000062320000
                    IE: Unknown: DD090040960E00004B690F
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
          Cell 06 - Address: 00:15:2B:21:D7:D1
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"YKDATA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000026e91599280
                    Extra: Last beacon: 1208ms ago
                    IE: Unknown: 0006594B44415441
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 050401020000
                    IE: Unknown: 0B0400000200
                    IE: Unknown: 2A0102
                    IE: Unknown: 3203304860
                    IE: Unknown: 851E000084000F00FF031900544E4B2D313233312D3200000000000000000025
                    IE: Unknown: AD0F00A0F8000009000000640000000000
                    IE: Unknown: DD06004096010102
                    IE: Unknown: DD050040960303
                    IE: Unknown: DD1600409604000207A4000023A400004243000062320000
                    IE: Unknown: DD090040960E00004B690F
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
          Cell 07 - Address: 00:15:2B:21:D7:D0
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000026e91580194
                    Extra: Last beacon: 1184ms ago
                    IE: Unknown: 000100
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 050400020000
                    IE: Unknown: 0B0400000200
                    IE: Unknown: 2A0102
                    IE: Unknown: 3203304860
                    IE: Unknown: 851E000084000F00FF031900544E4B2D313233312D3200000000000000000025
                    IE: Unknown: AD0F00A0F8000009000000640000000000
                    IE: Unknown: DD06004096010102
                    IE: Unknown: DD050040960303
                    IE: Unknown: DD1600409604000207A4000023A400004243000062320000
                    IE: Unknown: DD090040960E00004B690F
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00

eth0      Interface doesn't support scanning.

qwikrazor87@qwikrazor87-Latitude-D610:~/Desktop$ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true
qwikrazor87@qwikrazor87-Latitude-D610:~/Desktop$ sudo cat /var/log/syslog | grep -e b43 -e firmware -e wlan -e wpa -e etork | tail -n55
Nov 17 13:20:20 qwikrazor87-Latitude-D610 NetworkManager[643]: <info> (wlan0): supplicant interface state: ready -> inactive
Nov 17 14:17:42 qwikrazor87-Latitude-D610 kernel: [    1.438530] b43-pci-bridge 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Nov 17 14:17:42 qwikrazor87-Latitude-D610 kernel: [   19.464512] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
Nov 17 14:17:43 qwikrazor87-Latitude-D610 kernel: [   19.970922] Registered led device: b43-phy0::tx
Nov 17 14:17:43 qwikrazor87-Latitude-D610 kernel: [   19.971155] Registered led device: b43-phy0::rx
Nov 17 14:17:43 qwikrazor87-Latitude-D610 kernel: [   19.971405] Registered led device: b43-phy0::radio
Nov 17 14:17:43 qwikrazor87-Latitude-D610 NetworkManager[653]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:03:03.0/ssb0:0/net/wlan0, iface: wlan0)
Nov 17 14:17:43 qwikrazor87-Latitude-D610 NetworkManager[653]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:03:03.0/ssb0:0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Nov 17 14:17:43 qwikrazor87-Latitude-D610 NetworkManager[653]: <info> monitoring kernel firmware directory '/lib/firmware'.
Nov 17 14:17:43 qwikrazor87-Latitude-D610 NetworkManager[653]: <info> (wlan0): using nl80211 for WiFi device control
Nov 17 14:17:43 qwikrazor87-Latitude-D610 NetworkManager[653]: <warn> (wlan0): driver supports Access Point (AP) mode
Nov 17 14:17:43 qwikrazor87-Latitude-D610 NetworkManager[653]: <info> (wlan0): new 802.11 WiFi device (driver: 'b43' ifindex: 3)
Nov 17 14:17:43 qwikrazor87-Latitude-D610 NetworkManager[653]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Nov 17 14:17:43 qwikrazor87-Latitude-D610 NetworkManager[653]: <info> (wlan0): now managed
Nov 17 14:17:43 qwikrazor87-Latitude-D610 NetworkManager[653]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Nov 17 14:17:43 qwikrazor87-Latitude-D610 NetworkManager[653]: <info> (wlan0): bringing up device.
Nov 17 14:17:44 qwikrazor87-Latitude-D610 kernel: [   21.020060] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Nov 17 14:17:44 qwikrazor87-Latitude-D610 NetworkManager[653]: <info> (wlan0): preparing device.
Nov 17 14:17:44 qwikrazor87-Latitude-D610 NetworkManager[653]: <info> (wlan0): deactivating device (reason 'managed') [2]
Nov 17 14:17:44 qwikrazor87-Latitude-D610 dbus[453]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Nov 17 14:17:44 qwikrazor87-Latitude-D610 kernel: [   21.080713] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov 17 14:17:44 qwikrazor87-Latitude-D610 kernel: [   21.081041] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov 17 14:17:44 qwikrazor87-Latitude-D610 NetworkManager[653]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:03:03.0/ssb0:0/net/wlan0, iface: wlan0)
Nov 17 14:17:44 qwikrazor87-Latitude-D610 NetworkManager[653]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:03:03.0/ssb0:0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Nov 17 14:17:44 qwikrazor87-Latitude-D610 dbus[453]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Nov 17 14:17:44 qwikrazor87-Latitude-D610 NetworkManager[653]: <info> wpa_supplicant started
Nov 17 14:17:44 qwikrazor87-Latitude-D610 NetworkManager[653]: <info> (wlan0): supplicant interface state: starting -> ready
Nov 17 14:17:44 qwikrazor87-Latitude-D610 NetworkManager[653]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Nov 17 14:17:44 qwikrazor87-Latitude-D610 NetworkManager[653]: <info> (wlan0): supplicant interface state: ready -> inactive
Nov 17 14:41:09 qwikrazor87-Latitude-D610 kernel: [    1.450336] b43-pci-bridge 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Nov 17 14:41:10 qwikrazor87-Latitude-D610 NetworkManager[651]: <info> monitoring kernel firmware directory '/lib/firmware'.
Nov 17 14:41:10 qwikrazor87-Latitude-D610 kernel: [   20.468940] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
Nov 17 14:41:10 qwikrazor87-Latitude-D610 kernel: [   20.639151] Registered led device: b43-phy0::tx
Nov 17 14:41:10 qwikrazor87-Latitude-D610 kernel: [   20.639214] Registered led device: b43-phy0::rx
Nov 17 14:41:10 qwikrazor87-Latitude-D610 kernel: [   20.639278] Registered led device: b43-phy0::radio
Nov 17 14:41:11 qwikrazor87-Latitude-D610 NetworkManager[651]: <info> (wlan0): using nl80211 for WiFi device control
Nov 17 14:41:11 qwikrazor87-Latitude-D610 NetworkManager[651]: <warn> (wlan0): driver supports Access Point (AP) mode
Nov 17 14:41:11 qwikrazor87-Latitude-D610 NetworkManager[651]: <info> (wlan0): new 802.11 WiFi device (driver: 'b43' ifindex: 3)
Nov 17 14:41:11 qwikrazor87-Latitude-D610 NetworkManager[651]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Nov 17 14:41:11 qwikrazor87-Latitude-D610 NetworkManager[651]: <info> (wlan0): now managed
Nov 17 14:41:11 qwikrazor87-Latitude-D610 NetworkManager[651]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Nov 17 14:41:11 qwikrazor87-Latitude-D610 NetworkManager[651]: <info> (wlan0): bringing up device.
Nov 17 14:41:11 qwikrazor87-Latitude-D610 kernel: [   21.451477] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Nov 17 14:41:11 qwikrazor87-Latitude-D610 NetworkManager[651]: <info> (wlan0): preparing device.
Nov 17 14:41:11 qwikrazor87-Latitude-D610 NetworkManager[651]: <info> (wlan0): deactivating device (reason 'managed') [2]
Nov 17 14:41:11 qwikrazor87-Latitude-D610 kernel: [   21.528681] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov 17 14:41:11 qwikrazor87-Latitude-D610 kernel: [   21.529017] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov 17 14:41:11 qwikrazor87-Latitude-D610 dbus[454]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Nov 17 14:41:11 qwikrazor87-Latitude-D610 NetworkManager[651]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:03:03.0/ssb0:0/net/wlan0, iface: wlan0)
Nov 17 14:41:11 qwikrazor87-Latitude-D610 NetworkManager[651]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:03:03.0/ssb0:0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Nov 17 14:41:11 qwikrazor87-Latitude-D610 dbus[454]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Nov 17 14:41:11 qwikrazor87-Latitude-D610 NetworkManager[651]: <info> wpa_supplicant started
Nov 17 14:41:11 qwikrazor87-Latitude-D610 NetworkManager[651]: <info> (wlan0): supplicant interface state: starting -> ready
Nov 17 14:41:11 qwikrazor87-Latitude-D610 NetworkManager[651]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Nov 17 14:41:11 qwikrazor87-Latitude-D610 NetworkManager[651]: <info> (wlan0): supplicant interface state: ready -> inactive

```

---

### Post by wildmanne39 on 2012-11-17
Hi, which network are you trying to connect too?
Thanks

---

### Post by qwikrazor87 on 2012-11-17
LKSDWireless

---

### Post by wildmanne39 on 2012-11-17
Hi, there are two named that, you need to delete one of them, or remove all of them then reboot and let network manager find the connection that would be best.

The signal strength is only 50 percent that is not very good.

I would also set your routers encryption to just wpa2 if you have that option.
Thanks

---

### Post by qwikrazor87 on 2012-11-17
Hi.
The LKSDWireless I am using is a public access point so I can't change the encryption.

How can I remove the access points from my list or delete one of them?
Thank you.

---

### Post by wildmanne39 on 2012-11-17
Hi, click on the internet icon in the top right corner of the screen then click on edit connections and remove them, then reboot and let network manager find the connection.
Thanks

---

### Post by qwikrazor87 on 2012-11-17
Hi Wild Man.
Thank you so much! I am posting from within Xubuntu! You were so helpful! :D

---

### Post by wildmanne39 on 2012-11-17
Hi, your welcome! please use thread tools at the top of the page to mark the thread solved.
Enjoy

---

### Post by qwikrazor87 on 2012-11-17
Done.
Thank you once again!

---

### Post by wildmanne39 on 2013-03-15
Hi, this is the file you need.[ATTACH]240223[/ATTACH]

---

### Post by qwikrazor87 on 2013-03-16
Thank you Wild Man, much appreciated. :)

---

### Post by wildmanne39 on 2013-03-16
Your welcome!

---

