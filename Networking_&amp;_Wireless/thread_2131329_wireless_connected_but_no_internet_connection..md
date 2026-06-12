---
title: "wireless connected but no internet connection."
date: 2013-04-01
forum: Networking &amp; Wireless
---

### Post by 1teun on 2013-04-01
Hi all, Very similar questions have been asked and answered before, but I lack the technical understanding needed to extract my own answer from reading previous threats, so I hope someone is willing to help me out in my case.

I am running Lubuntu 12.10 on an old PB Dots laptop. Wifi always worked fine but since a few days it does appearantly connect to the wifi but I can't connect to any internetsites or run any updates or downloads. I am staying at my girlfriends house and don't have details about the wifi router/connection. Wifi works fine on my girlfriend's laptop which is also running Lubuntu 12.10. I am still able to connect with my own laptop using a LAN cable.

as it seems relevant i have input "ifconfig" in the terminal and got the following output:

```
teun@DOTS:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:5a:d8:fb:50  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4439 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4314 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:4045783 (4.0 MB)  TX bytes:686464 (686.4 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:625 errors:0 dropped:0 overruns:0 frame:0
          TX packets:625 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:49161 (49.1 KB)  TX bytes:49161 (49.1 KB)


wlan0     Link encap:Ethernet  HWaddr 00:25:56:6e:48:b9  
          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::225:56ff:fe6e:48b9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:137 errors:0 dropped:0 overruns:0 frame:0
          TX packets:420 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16794 (16.7 KB)  TX bytes:44738 (44.7 KB)
```

Thanks a lot for any replies. 
teun

---

### Post by praseodym on 2013-04-01
Please show additionally:
```
uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
cat /etc/network/interfaces
cat /etc/resolv.conf
iwconfig
route -n
rfkill list
sudo iwlist scan
```

---

### Post by 1teun on 2013-04-01
teun@DOTS:~$```
 uname -a
Linux DOTS 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:32:08 UTC 2012 i686 i686 i686 GNU/Linux
teun@DOTS:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
	Subsystem: Foxconn International, Inc. Device [105b:e00d]
	Kernel driver in use: ath5k
--
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8132 Fast Ethernet [1969:1062] (rev c0)
	Subsystem: Acer Incorporated [ALI] Device [1025:0241]
	Kernel driver in use: atl1c
teun@DOTS:~$ lsusb
Bus 001 Device 002: ID 04f2:b084 Chicony Electronics Co., Ltd 
Bus 003 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
teun@DOTS:~$ lsmod
Module                  Size  Used by
coretemp               13168  0 
joydev                 17161  0 
arc4                   12473  2 
snd_hda_codec_realtek    63356  1 
snd_hda_intel          32515  1 
snd_hda_codec         111547  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80163  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
microcode              18209  0 
snd_rawmidi            25382  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
psmouse                84843  0 
serio_raw              13031  0 
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
snd_timer              24411  2 snd_pcm,snd_seq
uvcvideo               71277  0 
videobuf2_core         32070  1 uvcvideo
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               95841  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12756  1 uvcvideo
ath5k                 135205  0 
i915                  457161  2 
ath                    19187  1 ath5k
videobuf2_memops       13184  1 videobuf2_vmalloc
acer_wmi               27586  0 
sparse_keymap          13658  1 acer_wmi
snd                    61991  11 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lpc_ich                16925  0 
mac80211              461161  1 ath5k
drm_kms_helper         45271  1 i915
drm                   230463  3 i915,drm_kms_helper
soundcore              14599  1 snd
cfg80211              175375  3 ath5k,ath,mac80211
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13197  1 i915
rfcomm                 37276  0 
parport_pc             31968  0 
bnep                   17707  2 
ppdev                  12817  0 
bluetooth             183228  10 rfcomm,bnep
video                  18847  2 acer_wmi,i915
wmi                    18590  1 acer_wmi
mac_hid                13037  0 
lp                     13299  0 
parport                40753  3 parport_pc,ppdev,lp
hid_generic            12445  0 
usbhid                 41702  0 
hid                    82142  2 hid_generic,usbhid
atl1c                  36175  0 
teun@DOTS:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
teun@DOTS:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
teun@DOTS:~$ iwconfig
wlan0     IEEE 802.11bg  ESSID:"phikli"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: CC:5D:4E:77:EF:77   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-32 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:27   Missed beacon:0


lo        no wireless extensions.


eth0      no wireless extensions.


teun@DOTS:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0
teun@DOTS:~$ rfkill list
0: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
teun@DOTS:~$ sudo iwlist scan
[sudo] password for teun: 
wlan0     Scan completed :
          Cell 01 - Address: CC:5D:4E:77:EF:77
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-34 dBm  
                    Encryption key:on
                    ESSID:"phikli"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000a5d45b47e8
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 00067068696B6C69
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 0706534720010D14
                    IE: Unknown: 200100
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
          Cell 02 - Address: 5C:D9:98:CA:75:A4
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"BALUR NG MGA SMURFS3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000038f7453146
                    Extra: Last beacon: 328ms ago
                    IE: Unknown: 001442414C5552204E47204D474120534D5552465333
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030103
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05060021127A
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706474220010D10
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD750050F204104A00011010440001021041000100103B0001031047001045D044E2EA60A5904DBC5CD998CA75A410210006442D4C696E6B102300074449522D363135102400074449522D3631351042000830303030303030301054000800060050F2040001101100074449522D363135100800020086
          Cell 03 - Address: B8:A3:86:9F:D7:38
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"a0706kc@unifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002a7a3a6e6c
                    Extra: Last beacon: 1624ms ago
                    IE: Unknown: 000D61303730366B6340756E696669
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030104
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000018127A
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706474220010D10
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD750050F204104A00011010440001021041000100103B00010310470010AD333808B84FB6C7245DB8A3869FD73810210006442D4C696E6B102300074449522D363135102400074449522D3631351042000830303030303030301054000800060050F2040001101100074449522D363135100800020086
          Cell 04 - Address: 00:1F:FB:2A:11:0E
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:on
                    ESSID:"2A110E"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002a7b76df46
                    Extra: Last beacon: 668ms ago
                    IE: Unknown: 0006324131313045
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6C0017FF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1609030700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010038127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: 0706393320090310
          Cell 05 - Address: CC:B2:55:06:A9:88
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"manik521"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000012d450149
                    Extra: Last beacon: 644ms ago
                    IE: Unknown: 00086D616E696B353231
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010A
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0502003E127A
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706474220010D10
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD750050F204104A00011010440001021041000100103B000103104700108014B200DC4776DAB799CCB25506A98810210006442D4C696E6B102300074449522D363135102400074449522D3631351042000830303030303030301054000800060050F2040001101100074449522D363135100800020080
          Cell 06 - Address: 34:08:04:C6:9A:A4
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"DedyAnry"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002e779fb16b
                    Extra: Last beacon: 708ms ago
                    IE: Unknown: 000844656479416E7279
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030109
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD130050F204104A00011010440001021041000100
                    IE: Unknown: 050400010008
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1609070600000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
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
                    IE: Unknown: 0B0504001A127A
                    IE: Unknown: DD07000C4307000000
          Cell 07 - Address: BC:F6:85:D2:E4:90
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"leesiew@unifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000007cd466206f
                    Extra: Last beacon: 600ms ago
                    IE: Unknown: 000D6C65657369657740756E696669
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000057127A
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706474220010D10
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD750050F204104A00011010440001021041000100103B000103104700106953EB2512FFD79A6004BCF685D2E49010210006442D4C696E6B102300074449522D363135102400074449522D3631351042000830303030303030301054000800060050F2040001101100074449522D363135100800020080


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.
```


teun@DOTS:~$

---

### Post by praseodym on 2013-04-01
Deactivate the hardware encryption of the driver:
```

echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
```
and try WPA2-AES encryption.

---

### Post by 1teun on 2013-04-01
I entered the code in the terminal and got the following output:

teun@DOTS:~$```
 echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
[sudo] password for teun: 
options ath5k nohwcrypt=1
teun@DOTS:~$ sudo modprobe -rfv ath5k
rmmod /lib/modules/3.5.0-17-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
rmmod /lib/modules/3.5.0-17-generic/kernel/drivers/net/wireless/ath/ath.ko
rmmod /lib/modules/3.5.0-17-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.5.0-17-generic/kernel/net/wireless/cfg80211.ko
teun@DOTS:~$ sudo modprobe -v ath5k
insmod /lib/modules/3.5.0-17-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.5.0-17-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.5.0-17-generic/kernel/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/3.5.0-17-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko nohwcrypt=1
```


The effect it had puzzles me: after I entered a word into the chromium adresbar the google page with search results would load normally. When I clicked on any link or enter any web adress (including [www.google.com](www.google.com)) I couldn't access the page and got:[COLOR=#000000][FONT=Helvetica]"The webpage at **[http://google.com/](http://google.com/)** might be temporarily down or it may have moved permanently to a new web address."

Then I connected the LAN cable for a few minutes, unplugged it again, and now the google search results will not load anymore from the adressbar and I seem to be back where I started.

Please note that my knowledge is quite limited. I am not sure what action to preform in order to "try WPA2-AES encryption."[/FONT][/COLOR]
[COLOR=#777777][FONT=Helvetica]
[/FONT][/COLOR]

---

### Post by praseodym on 2013-04-01
Add the IP of your router into your browser and login to the router interface. Check the following settings:

 * Wireless mode: "b+g"

 * Set the channel fixed to "1"

 * Network to "broadcast", not "hidden"

 * Change to WPA2-AES (CCMP) encryption

Is "PB dots" a brand of Acer?

---

### Post by 1teun on 2013-04-01
Found my way into the router (zyxel p-600) interface, but can't find a "wireless mode" setting. 
I also can't find where to set network to "broadcast.
The "security mode" only let me choose between WPA2-psk or simply WPA2. I tried WPA2 but can't save this setting because it tells me: "Authentication Server IP format error!"

I am afraid to experiment with the router settings because I don't want other users of the connection to have problems because of me.

Dot S is a type of netbook by Packard Bell, I guess I wasn't clear on that before.

Unfortunatly I will have to continue trying tomorrow, much thanks for your support so far Praseodym!

---

### Post by praseodym on 2013-04-01
WPA2-PSK should be the right one. How long is your key? It should be at least 8 characters. Is Packard Bell from Acer now? Alternatively, try Wicd instead of the network-manager to connect.

---

### Post by wildmanne39 on 2013-04-01
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by 1teun on 2013-04-02
I am testing the wifi in a cafe now and here it works fine. (it's open, no networkkey or anything)

The network key in the house is 13 digits and letters long.

I googled and you are right, Packard Bell is now part of Acer.

I will try Wicd later today and post the results.

(sorry about not boxing the code before)

---

### Post by 1teun on 2013-04-02
Ok, I installed Wicd but it doesn't make any difference.&nbsp;<br><br>I don't really want to change the router settings because it doesn't belong to me, and all other devices connect to wifi without a problem.<br><br>Any other suggestions?

---

### Post by steeldriver on 2013-04-02
It's difficult to tell from the symptoms you are describing but sometimes these flaky web page connection issues are due to fragmentation (or specifically how intermediate routers handle it) - sometimes they can be fixed by reducing the connection MTU

You could perform a ping test to see if that's a possible issue or you could just go ahead and reduce the MTU and see what happens - I don't know where that is in wicd, in nm you can do it by editing the connection properties, or you can use ifconfig to set the MTU temporarily

[http://ubuntuforums.org/showthread.php?t=2071761&p=12302694#post12302694](http://ubuntuforums.org/showthread.php?t=2071761&p=12302694#post12302694)

[http://ubuntuforums.org/showthread.php?t=2119791&p=12531403#post12531403](http://ubuntuforums.org/showthread.php?t=2119791&p=12531403#post12531403)

---

### Post by 1teun on 2013-04-04
Ok, I did the ping test with different MTU values as shown in the previous thread, and found that 1429 and higher it resulted in "frag needed".
so I removed the wicd package and changed he MTU in the network manager to 1456. But I still can't connect to the Internet. I tried lower MTU values too but it doesn't make a difference.

---

### Post by praseodym on 2013-04-05
Contact your provider, which MTU is used.

---

