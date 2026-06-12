---
title: "WiFI Connecting"
date: 2011-08-19
forum: Networking &amp; Wireless
---

### Post by zu5be on 2011-08-19
Hello
I installed Ubuntu yesterday. When i am trying to connect wifi its repeatedly not accepting the password(wifi) after couple of tries when it does, the connectivity remains for several seconds. I mean i can open only the first page of a website and later the connectivity is lost(cant open webpages or download, but the internet is still connected. Thanks

ThinkPad
sl410k
Realtec rtl8187

---

### Post by fdrake on 2011-08-19
> **zu5be said:**
> Hello
I installed Ubuntu yesterday. When i am trying to connect wifi its repeatedly not accepting the password(wifi) after couple of tries when it does, the connectivity remains for several seconds. I mean i can open only the first page of a website and later the connectivity is lost(cant open webpages or download, but the internet is still connected. Thanks

ThinkPad
sl410k
Realtec rtl8187
 post here:

```

less /etc/lsb-release
iwconfig
lspci | grep Wireless
dmesg | grep wlan0

```

---

### Post by zu5be on 2011-08-21
I am having an in build wifi adapter and a usb wifi card. 
When i try to connect the inbuild one, it works fine but the usb one connects easily but after few seconds there is no transfer of data( i cant open or surf internet). the internet is still connected. Below are some details.

1 less /etc/lsb-release

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"

2 iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bg  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.457 GHz  Access Point: Not-Associated   
          Bit Rate:12 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan1     IEEE 802.11bg  ESSID:"TP-LINK_38B2C8"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:23:CD:38:B2:C8   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=52/70  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:418  Invalid misc:6   Missed beacon:0

3 lspci | grep Wireless
05:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)

4 dmesg | grep wlan1&#65288; nothing happens on wlan0)
05:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)
zu5be@zu5be-ThinkPad-SL410:~$ dmesg | grep wlan0
zu5be@zu5be-ThinkPad-SL410:~$ dmesg | grep wlan1
[ 2174.720725] wlan1: authenticate with 00:23:cd:38:b2:c8 (try 1)
[ 2174.722234] wlan1: authenticated
[ 2174.828987] wlan1: associate with 00:23:cd:38:b2:c8 (try 1)
[ 2174.842975] wlan1: RX AssocResp from 00:23:cd:38:b2:c8 (capab=0x431 status=0 aid=111)
[ 2174.842981] wlan1: associated
[ 2228.209249] wlan1: deauthenticating from 00:23:cd:38:b2:c8 by local choice (reason=3)
[ 2230.548823] wlan1: authenticate with d8:5d:4c:54:60:14 (try 1)
[ 2230.748056] wlan1: authenticate with d8:5d:4c:54:60:14 (try 2)
[ 2230.750608] wlan1: authenticated
[ 2230.865170] wlan1: associate with d8:5d:4c:54:60:14 (try 1)
[ 2230.867430] wlan1: RX AssocResp from d8:5d:4c:54:60:14 (capab=0x431 status=0 aid=21)
[ 2230.867435] wlan1: associated
[ 2343.052433] wlan1: deauthenticating from d8:5d:4c:54:60:14 by local choice (reason=3)
[ 2494.776706] wlan1: authenticate with 00:23:cd:38:b2:c8 (try 1)
[ 2494.976058] wlan1: authenticate with 00:23:cd:38:b2:c8 (try 2)
[ 2494.978716] wlan1: authenticated
[ 2495.097355] wlan1: associate with 00:23:cd:38:b2:c8 (try 1)
[ 2495.099600] wlan1: RX AssocResp from 00:23:cd:38:b2:c8 (capab=0x431 status=0 aid=111)
[ 2495.099605] wlan1: associated
[ 2744.612066] ieee80211 phy3: wlan1: No probe response from AP 00:23:cd:38:b2:c8 after 500ms, disconnecting.
[ 2746.993012] wlan1: authenticate with 00:23:cd:38:b2:c8 (try 1)
[ 2746.994522] wlan1: authenticated
[ 2747.104883] wlan1: associate with 00:23:cd:38:b2:c8 (try 1)
[ 2747.107382] wlan1: RX AssocResp from 00:23:cd:38:b2:c8 (capab=0x431 status=0 aid=111)
[ 2747.107388] wlan1: associated

---

### Post by zu5be on 2011-08-21
> **fdrake said:**
> post here:

```

less /etc/lsb-release
iwconfig
lspci | grep Wireless
dmesg | grep wlan0

```


I am having an in build wifi adapter and a usb wifi card. 
When i try to connect the inbuild one, it works fine but the usb one connects easily but after few seconds there is no transfer of data( i cant open or surf internet). the internet is still connected. Below are some details.

1 less /etc/lsb-release

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"

2 iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bg  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.457 GHz  Access Point: Not-Associated   
          Bit Rate:12 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan1     IEEE 802.11bg  ESSID:"TP-LINK_38B2C8"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:23:CD:38:B2:C8   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=52/70  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:418  Invalid misc:6   Missed beacon:0

3 lspci | grep Wireless
05:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)

4 dmesg | grep wlan1&#65288; nothing happens on wlan0)
05:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)
zu5be@zu5be-ThinkPad-SL410:~$ dmesg | grep wlan0
zu5be@zu5be-ThinkPad-SL410:~$ dmesg | grep wlan1
[ 2174.720725] wlan1: authenticate with 00:23:cd:38:b2:c8 (try 1)
[ 2174.722234] wlan1: authenticated
[ 2174.828987] wlan1: associate with 00:23:cd:38:b2:c8 (try 1)
[ 2174.842975] wlan1: RX AssocResp from 00:23:cd:38:b2:c8 (capab=0x431 status=0 aid=111)
[ 2174.842981] wlan1: associated
[ 2228.209249] wlan1: deauthenticating from 00:23:cd:38:b2:c8 by local choice (reason=3)
[ 2230.548823] wlan1: authenticate with d8:5d:4c:54:60:14 (try 1)
[ 2230.748056] wlan1: authenticate with d8:5d:4c:54:60:14 (try 2)
[ 2230.750608] wlan1: authenticated
[ 2230.865170] wlan1: associate with d8:5d:4c:54:60:14 (try 1)
[ 2230.867430] wlan1: RX AssocResp from d8:5d:4c:54:60:14 (capab=0x431 status=0 aid=21)
[ 2230.867435] wlan1: associated
[ 2343.052433] wlan1: deauthenticating from d8:5d:4c:54:60:14 by local choice (reason=3)
[ 2494.776706] wlan1: authenticate with 00:23:cd:38:b2:c8 (try 1)
[ 2494.976058] wlan1: authenticate with 00:23:cd:38:b2:c8 (try 2)
[ 2494.978716] wlan1: authenticated
[ 2495.097355] wlan1: associate with 00:23:cd:38:b2:c8 (try 1)
[ 2495.099600] wlan1: RX AssocResp from 00:23:cd:38:b2:c8 (capab=0x431 status=0 aid=111)
[ 2495.099605] wlan1: associated
[ 2744.612066] ieee80211 phy3: wlan1: No probe response from AP 00:23:cd:38:b2:c8 after 500ms, disconnecting.
[ 2746.993012] wlan1: authenticate with 00:23:cd:38:b2:c8 (try 1)
[ 2746.994522] wlan1: authenticated
[ 2747.104883] wlan1: associate with 00:23:cd:38:b2:c8 (try 1)
[ 2747.107382] wlan1: RX AssocResp from 00:23:cd:38:b2:c8 (capab=0x431 status=0 aid=111)
[ 2747.107388] wlan1: associated

---

### Post by Actonix on 2011-08-21
Looks like might be some interference from another Wifi access point close to you, might want to try changing channel

---

### Post by fdrake on 2011-08-21
> **zu5be said:**
> I am having an in build wifi adapter and a usb wifi card. 
When i try to connect the inbuild one, it works fine but the usb one connects easily but after few seconds there is no transfer of data( i cant open or surf internet). the internet is still connected. Below are some details.

1 less /etc/lsb-release

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"

2 iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bg  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.457 GHz  Access Point: Not-Associated   
          Bit Rate:12 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan1     IEEE 802.11bg  ESSID:"TP-LINK_38B2C8"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:23:CD:38:B2:C8   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=52/70  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:418  Invalid misc:6   Missed beacon:0

3 lspci | grep Wireless
05:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)

4 dmesg | grep wlan1&#65288; nothing happens on wlan0)
05:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)
zu5be@zu5be-ThinkPad-SL410:~$ dmesg | grep wlan0
zu5be@zu5be-ThinkPad-SL410:~$ dmesg | grep wlan1
[ 2174.720725] wlan1: authenticate with 00:23:cd:38:b2:c8 (try 1)
[ 2174.722234] wlan1: authenticated
[ 2174.828987] wlan1: associate with 00:23:cd:38:b2:c8 (try 1)
[ 2174.842975] wlan1: RX AssocResp from 00:23:cd:38:b2:c8 (capab=0x431 status=0 aid=111)
[ 2174.842981] wlan1: associated
[ 2228.209249] wlan1: deauthenticating from 00:23:cd:38:b2:c8 by local choice (reason=3)
[ 2230.548823] wlan1: authenticate with d8:5d:4c:54:60:14 (try 1)
[ 2230.748056] wlan1: authenticate with d8:5d:4c:54:60:14 (try 2)
[ 2230.750608] wlan1: authenticated
[ 2230.865170] wlan1: associate with d8:5d:4c:54:60:14 (try 1)
[ 2230.867430] wlan1: RX AssocResp from d8:5d:4c:54:60:14 (capab=0x431 status=0 aid=21)
[ 2230.867435] wlan1: associated
[ 2343.052433] wlan1: deauthenticating from d8:5d:4c:54:60:14 by local choice (reason=3)
[ 2494.776706] wlan1: authenticate with 00:23:cd:38:b2:c8 (try 1)
[ 2494.976058] wlan1: authenticate with 00:23:cd:38:b2:c8 (try 2)
[ 2494.978716] wlan1: authenticated
[ 2495.097355] wlan1: associate with 00:23:cd:38:b2:c8 (try 1)
[ 2495.099600] wlan1: RX AssocResp from 00:23:cd:38:b2:c8 (capab=0x431 status=0 aid=111)
[ 2495.099605] wlan1: associated
[ 2744.612066] ieee80211 phy3: wlan1: No probe response from AP 00:23:cd:38:b2:c8 after 500ms, disconnecting.
[ 2746.993012] wlan1: authenticate with 00:23:cd:38:b2:c8 (try 1)
[ 2746.994522] wlan1: authenticated
[ 2747.104883] wlan1: associate with 00:23:cd:38:b2:c8 (try 1)
[ 2747.107382] wlan1: RX AssocResp from 00:23:cd:38:b2:c8 (capab=0x431 status=0 aid=111)
[ 2747.107388] wlan1: associated

ok,, your post is a little bit different from your first one. so you don't have any problem with the build-in wifi than right, only with the usb-one?

---

### Post by praseodym on 2011-08-21
Hello,

can you post the following outputs:
```

lsmod
lspci -nnk | grep -iA2 net
rfkill list
sudo iwlist scan
```

Changing the channel is a good idea, because both wlan0 and wlan1 are on the same frequency 2.457 GHz

---

### Post by bkratz on 2011-08-21
> **praseodym said:**
> Hello,

can you post the following outputs:
```

lsmod
lspci -nnk | grep -iA2 net
rfkill list
sudo iwlist scan
```

Changing the channel is a good idea, because both wlan0 and wlan1 are on the same frequency 2.457 GHz


I believe network manager would have problems with two wifi adapters active at the same time. lsusb would tell what the usb adapter is. I think the internal probably will either have to be diabled in the bios or the drivers blacklisted before the usb one will reliably connect.

---

### Post by zu5be on 2011-08-21
> **bkratz said:**
> I believe network manager would have problems with two wifi adapters active at the same time. lsusb would tell what the usb adapter is. I think the internal probably will either have to be diabled in the bios or the drivers blacklisted before the usb one will reliably connect.

Could any one tell How to disable the internal adapter or blacklist the drivers?

---

### Post by bkratz on 2011-08-21
Please post the output of 

lsmod | grep 819

---

### Post by zu5be on 2011-08-21
> **praseodym said:**
> Hello,

can you post the following outputs:
```

lsmod
lspci -nnk | grep -iA2 net
rfkill list
sudo iwlist scan
```

Changing the channel is a good idea, because both wlan0 and wlan1 are on the same frequency 2.457 GHz

I triled to change channels (still the frequency is same, when the usb card is not connected it has a different frequency, when i connect it. it changes to the same as 2.457 GHz.

below are the outputs.


zu5be@zu5be-ThinkPad-SL410:~$ [COLOR="Red"]lsmod[/COLOR]
Module                  Size  Used by
cryptd                 19801  0 
aes_i586               16956  0 
aes_generic            38023  1 aes_i586
parport_pc             32111  0 
ppdev                  12849  0 
vesafb                 13449  1 
arc4                   12473  2 
binfmt_misc            13213  1 
rtl8187                56206  0 
snd_hda_codec_hdmi     27535  1 
snd_hda_codec_realtek   255882  1 
mac80211              257001  1 rtl8187
snd_hda_intel          24113  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
fglrx                2434640  108 
thinkpad_acpi          73750  0 
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
r8192se_pci           482505  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               66851  0 
eeprom_93cx6           12653  1 rtl8187
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               75143  1 uvcvideo
joydev                 17322  0 
jmb38x_ms              17364  0 
cfg80211              156212  3 rtl8187,mac80211,r8192se_pci
psmouse                73312  0 
snd                    55295  15 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,thinkpad_acpi,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nvram                  14035  1 thinkpad_acpi
memstick               15816  1 jmb38x_ms
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
video                  18951  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
ahci                   21591  3 
libahci                25548  1 ahci
r8169                  42534  0 
sdhci_pci              13623  0 
sdhci                  22720  1 sdhci_pci

zu5be@zu5be-ThinkPad-SL410:~$ [COLOR="red"]lspci -nnk | grep -iA2 net[/COLOR]
05:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev 10)
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:e020]
	Kernel driver in use: rtl819xSE
--
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
	Subsystem: Lenovo Device [17aa:2131]
	Kernel driver in use: r8169


zu5be@zu5be-ThinkPad-SL410:~$ [COLOR="red"]sudo iwlist scan[/COLOR]
[sudo] password for zu5be: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: C8:3A:35:05:3E:E8
                    ESSID:"lee_2404"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=47/100  Signal level=-75 dBm  Noise level=-93 dBm
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 106ms ago
          Cell 02 - Address: B0:48:7A:1E:FE:8E
                    ESSID:"cmexm"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:150 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54 
                    Quality=59/100  Signal level=-74 dBm  Noise level=-99 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 116ms ago
          Cell 03 - Address: E0:05:C5:B7:D9:AC
                    ESSID:"TP-LINK_1101"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 9 11 6 12 18 24 36 48 54 
                    Quality=47/100  Signal level=-73 dBm  Noise level=-93 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    Extra: Last beacon: 130ms ago
          Cell 04 - Address: 00:23:CD:38:B2:C8
                    ESSID:"TP-LINK_38B2C8"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:10
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 9 11 6 12 18 24 36 48 54 
                    Quality=47/100  Signal level=-75 dBm  Noise level=-93 dBm
                    Extra: Last beacon: 81ms ago
          Cell 05 - Address: 00:21:91:4A:2E:08
                    ESSID:"kdi"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54 
                    Quality=47/100  Signal level=-73 dBm  Noise level=-93 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 139ms ago
          Cell 06 - Address: 00:25:86:79:B8:04
                    ESSID:"Lina"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 9 11 6 12 18 24 36 48 54 
                    Quality=47/100  Signal level=-73 dBm  Noise level=-93 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    Extra: Last beacon: 201ms ago
          Cell 07 - Address: 00:1E:58:0D:F8:EA
                    ESSID:"MNF"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 48 18 24 36 54 
                    Quality=47/100  Signal level=-73 dBm  Noise level=-93 dBm
                    Extra: Last beacon: 140ms ago

wlan1     Scan completed :
          Cell 01 - Address: 00:23:CD:38:B2:C8
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_38B2C8"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001326d1e85
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 000E54502D4C494E4B5F333842324338
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010A
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: Unknown: DD0900037F01010008FF7F
                    IE: Unknown: DD1A00037F03010000000023CD38B2C80223CD38B2C864002C010808
          Cell 02 - Address: 06:1B:B1:20:6C:E5
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"JCJ-2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000d5ffdb8f8
                    Extra: Last beacon: 1004ms ago
                    IE: Unknown: 00054A434A2D32
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706434E49010D1E
                    IE: Unknown: 200100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101040003A4000027A4000042435E0062322F00
                    IE: Unknown: 331A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 34160B080800000000000000000000000000000000000000
                    IE: Unknown: 3D160B080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000
          Cell 03 - Address: 00:23:CD:49:2F:98
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"FAST"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000013c4c8150e
                    Extra: Last beacon: 992ms ago
                    IE: Unknown: 000446415354
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 0706434E20010D14
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

---

### Post by bkratz on 2011-08-21
This will be temporary to see if it is worth following up with the blacklist, a reboot will add the module back in.

rmmod -f r8192se_pci

If it helps the other wireless we will make it permanent

---

### Post by nm_geo on 2011-08-21
My message was removed reason:  redundant.

---

### Post by praseodym on 2011-08-21
There are two wireless moduls loaded **rtl8187** and **r8192se_pci**:
Do you have two devices? Both wlan0 and wlan1 show activity! Please show:

```
lsusb
```

---

### Post by zu5be on 2011-08-22
> **praseodym said:**
> There are two wireless moduls loaded **rtl8187** and **r8192se_pci**:
Do you have two devices? Both wlan0 and wlan1 show activity! Please show:

```
lsusb
```

Yes, one is inbuilt and the other is usb one. The internal works fine but the usb one is not able to. I does connect but i cant surf internet or i mean no connectivity

---

### Post by zu5be on 2011-08-22
> **bkratz said:**
> This will be temporary to see if it is worth following up with the blacklist, a reboot will add the module back in.

rmmod -f r8192se_pci

If it helps the other wireless we will make it permanent

Tried it, but the prob is still there. 
I dont want to give up on Ubuntu.... coz i am loving it. Help pls

---

### Post by praseodym on 2011-08-22
Maybe both drivers dont work in parallel:

```
sudo modprobe -rf r8192se_pci rtl8187
sudo modprobe -v rtl8187
```
Remove the stick, re-plug it and try it again.

---

### Post by zu5be on 2011-08-22
> **praseodym said:**
> Maybe both drivers dont work in parallel:

```
sudo modprobe -rf r8192se_pci rtl8187
sudo modprobe -v rtl8187
```
Remove the stick, re-plug it and try it again.

working like a charm:) Thanks a lot 
Is this permanant or i have to do it every time?
will i be able to use inbuilt wifi anymore? How?
[COLOR="Red"]You people rock[/COLOR]:guitar::guitar:

---

### Post by praseodym on 2011-08-22
You can automatize it with a script. If you plug-in the stick, the module for the interior device is unloaded and vice versa:

```
gksudo gedit /etc/udev/rules.d/10-wlan-stick.rules 
```
Copy the following into it:

```
# UDEV-rule for external WLAN-sticks
# unloads/loads driver for int. WLAN-device

ACTION=="add", GOTO="device_check"
ACTION=="remove", GOTO="onboard_load"

LABEL="device_check
### WLAN-stick accepted, Onboard-card deactivated
BUS=="usb", KERNEL=="wlan*" RUN+="/sbin/modprobe -rf r8192se_pci"

GOTO="rules_end"

LABEL="onboard_load"
### WLAN-stick out, Onboard-card activated
BUS=="usb", KERNEL=="wlan*" RUN+="/sbin/modprobe r8192se_pci"

LABEL="rules_end"
```
save and exit. Reload udev:

```
sudo service udev reload
```

Inspired by [this]("http://forum.ubuntuusers.de/topic/wlan-usb-8194/#post-3133322") Thread.

---

### Post by zu5be on 2011-08-25
> **praseodym said:**
> You can automatize it with a script. If you plug-in the stick, the module for the interior device is unloaded and vice versa:

```
gksudo gedit /etc/udev/rules.d/10-wlan-stick.rules 
```
Copy the following into it:

```
# UDEV-rule for external WLAN-sticks
# unloads/loads driver for int. WLAN-device

ACTION=="add", GOTO="device_check"
ACTION=="remove", GOTO="onboard_load"

LABEL="device_check
### WLAN-stick accepted, Onboard-card deactivated
BUS=="usb", KERNEL=="wlan*" RUN+="/sbin/modprobe -rf r8192se_pci"

GOTO="rules_end"

LABEL="onboard_load"
### WLAN-stick out, Onboard-card activated
BUS=="usb", KERNEL=="wlan*" RUN+="/sbin/modprobe r8192se_pci"

LABEL="rules_end"
```
save and exit. Reload udev:

```
sudo service udev reload
```

Inspired by [this]("http://forum.ubuntuusers.de/topic/wlan-usb-8194/#post-3133322") Thread.

Hello
The command works only when i first use this one
sudo modprobe -rf r8192se_pci rtl8187
sudo modprobe -v rtl8187

sometimes the connection connects ok, but the speed is very slow. sometimes just keeps asking password again and again.
i am praying for a solution to this...:(

---

