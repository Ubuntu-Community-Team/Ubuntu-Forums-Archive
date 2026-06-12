---
title: "Also WNA1100 problems, other threats don't offer a solution"
date: 2011-08-28
forum: Networking &amp; Wireless
---

### Post by Robkg on 2011-08-28
First, I'm a noob, installed unbuntu a while ago, moved, got an office laptop and didn connect my pc. Now I wanted to connect it again, but I needed WiFi, because of the location of my pc. 

So I bought the WNA1100. I tried to install it a described in other threats, then it did not work. I tried to TS it, but that did not work either. 

Now the blue light is flashing from time to time, but I can't see any networks. Am I looking in the wrong place (where can I actually see/search for networks). I'm running Ubuntu 11.04. 

Just tell me which outputs to post here and I will. 

btw, rfkill list all doesn't return anything?

---

### Post by praseodym on 2011-08-28
Hello,

you may update the firmware for this driver via wired connection (copy/paste):

```
wget http://media.cdn.ubuntu-de.org/forum/attachments/2640681/ath_htc_firmware-1.tar.gz
sudo tar xvf ath_htc_firmware-1.tar.gz -C /lib/firmware 
```
and reload the driver:

```
sudo modprobe -rf ath9k_htc
sudo modprobe -v ath9k_htc
sudo service network-manager restart
```
Controls:

```
dmesg | grep ath
iwconfig
sudo iwlist scan
lsmod
```

---

### Post by Robkg on 2011-08-28
```
dmesg | grep ath
[    1.088548] device-mapper: multipath: version 1.2.0 loaded
[    1.088555] device-mapper: multipath round-robin: version 1.0.0 loaded
[   22.785585] ndiswrapper: driver netathuw (,11/25/2009,7.7.0.71) loaded
[   24.837407] wlan0: ethernet device e0:91:f5:53:f6:30 using NDIS driver: netathuw, version: 0x70007, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9030.F.conf
[ 1589.845017] usbcore: registered new interface driver ath9k_hif_usb
[ 1628.488084] usbcore: deregistering interface driver ath9k_hif_usb
[ 1628.488151] ath9k_htc: Driver unloaded
[ 1639.298089] usbcore: registered new interface driver ath9k_hif_usb

```

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

``````
sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: BC:AE:C5:00:A3:52
                    ESSID:"UPC104"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:12/100  Signal level:-88 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:22:3F:8C:C9:38
                    ESSID:"WindmillCon"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.417 GHz (Channel 2)
                    Quality:50/100  Signal level:-64 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:13:10:0A:F1:E6
                    ESSID:"estelleo"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality:21/100  Signal level:-82 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: 00:19:CB:F5:4F:68
                    ESSID:"5thPrivate"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.432 GHz (Channel 5)
                    Quality:15/100  Signal level:-86 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: 00:24:B2:8B:29:EC
                    ESSID:"NETGEARJB"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:40/100  Signal level:-70 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: 00:18:C2:01:05:BE
                    ESSID:"DockNet"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.442 GHz (Channel 7)
                    Quality:14/100  Signal level:-87 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 07 - Address: 00:1A:70:A2:9E:18
                    ESSID:"rogerson"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.457 GHz (Channel 10)
                    Quality:9/100  Signal level:-90 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 08 - Address: 00:26:4D:EC:9D:38
                    ESSID:"VodafoneSharingDock_EC9D48"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.442 GHz (Channel 7)
                    Quality:4/100  Signal level:-93 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 09 - Address: 00:22:3F:0D:31:42
                    ESSID:"Savagehouse"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality:4/100  Signal level:-93 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: 94:44:52:0A:96:76
                    ESSID:"tronket"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:7/100  Signal level:-91 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: 00:1B:11:8C:78:76
                    ESSID:"Windmill Apt"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:6/100  Signal level:-92 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: 00:19:5B:7F:C8:2A
                    ESSID:"PubDirAp001"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality:1/100  Signal level:-95 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

``````
lsmod
Module                  Size  Used by
ath9k_htc              55795  0 
mac80211              257001  1 ath9k_htc
ath9k_common           13611  1 ath9k_htc
ath9k_hw              300328  2 ath9k_htc,ath9k_common
ath                    19141  2 ath9k_htc,ath9k_hw
cfg80211              156212  3 ath9k_htc,mac80211,ath
nls_utf8               12493  1 
isofs                  39571  1 
vesafb                 13449  1 
snd_intel8x0           33213  1 
snd_ac97_codec        105614  1 snd_intel8x0
snd_hda_codec_hdmi     27479  1 
ac97_bus               12642  1 snd_ac97_codec
snd_hda_intel          24140  0 
snd_hda_codec          90901  2 snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  5 snd_intel8x0,snd_hda_codec_hdmi,snd_ac97_codec,snd_hda_intel,snd_hda_codec
joydev                 17322  0 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
binfmt_misc            13213  1 
snd_seq_midi_event     14475  1 snd_seq_midi
hid_microsoft          12745  0 
fglrx                2434640  131 
ppdev                  12849  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
usbhid                 41704  0 
ndiswrapper           192828  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
hid                    77084  2 hid_microsoft,usbhid
psmouse                73312  0 
snd                    55295  13 snd_intel8x0,snd_hda_codec_hdmi,snd_ac97_codec,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             32111  1 
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14073  3 snd_intel8x0,snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
usb_storage            43946  1 
uas                    17676  0 
floppy                 60032  0 
tg3                   131476  0 

```

So I see now that he finds some networks, how do I connect to the network that I want? (WindmillCon) (yes you are with stupid now :P). How do I do it in the terminal and how without? 

Btw, thanks for you quick responds!

---

### Post by praseodym on 2011-08-28
Did you see the networks after installing the firmware? If so, you dont need ndiswrapper anymore. You have to uninstall it completely for the native driver to work properly (copy/paste again):

```
sudo modprobe -rf ndiswrapper ath9k_htc
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
sudo modprobe -v ath9k_htc
```
Richt-klick on the network-manager applet->Edit Connection->Wireless

There you can setup a new connection by adding your ESSID and password. Use the type of encryption your router is broadcasting under "Network security".

Which network of the listed ones is yours? You should prefer WPA2-AES encryption for security reasons.

---

### Post by Robkg on 2011-08-28
> **praseodym said:**
> Did you see the networks after installing the firmware? If so, you dont need ndiswrapper anymore. You have to uninstall it completely for the native driver to work properly (copy/paste again):

```
sudo modprobe -rf ndiswrapper ath9k_htc
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
sudo modprobe -v ath9k_htc
```
Richt-klick on the network-manager applet->Edit Connection->Wireless

There you can setup a new connection by adding your ESSID and password. Use the type of encryption your router is broadcasting under "Network security".

Which network of the listed ones is yours? You should prefer WPA2-AES encryption for security reasons.
This one is mine: ```
Cell 02 - Address: 00:22:3F:8C:C9:38
                    ESSID:"WindmillCon"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.417 GHz (Channel 2)
                    Quality:50/100  Signal level:-64 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
```

When I enter the details, it does not connect?

---

### Post by praseodym on 2011-08-28
The encryption mode should be "WPA & WPA2 Personal". You may setup a new connection (Modus: Infrastructure) after deleting the current profile. Can you show:

```
sudo service network-manager restart
iwconfig
cat /etc/resolv.conf
route -n
```

---

### Post by Robkg on 2011-08-28
> **praseodym said:**
> The encryption mode should be "WPA & WPA2 Personal". You may setup a new connection (Modus: Infrastructure) after deleting the current profile. Can you show:

```
sudo service network-manager restart
iwconfig
cat /etc/resolv.conf
route -n
```

```
robkg:~$ sudo service network-manager restart
network-manager start/running, process 2156
robkg:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
robkg:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.1.1
robkg:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```

---

### Post by walt.smith1960 on 2011-08-28
I don't know if you've tried this, it's worked for me with 10.04 &10.10.  Two stage process, first install the app then run the app found under applications > system tools.  The second process has to be run after each kernel (image) upgrade. I also didn't try anything else before running this software.  I don't know if trying other things first will cause problems with this app or not.

[http://sourceforge.net/projects/ath9k-htc/](http://sourceforge.net/projects/ath9k-htc/)

---

### Post by nm_geo on 2011-08-28
I bought one of these just to do some testing, and I thought I had a very good solution to getting it going.  However, I had upgraded by Natty kernel to 3.0 just because I like to be on the so-called cutting edge.

Here is some pretty reviling information doing modinfo on the ath9k_htc in different Natty kernels.

```
~$ sudo modinfo ath9k_htc
filename:       /lib/modules/**2.6.38-11-generic/kernel/**drivers/net/wireless/ath/ath9k/ath9k_htc.ko
[B]firmware:       ar9271.fw
firmware:       ar7010_1_1.fw
firmware:       ar7010.fw[/B]
description:    Atheros driver 802.11n HTC based wireless devices
license:        Dual BSD/GPL
author:         Atheros Communications
srcversion:     8F244C9A8C97C1B3B163005
alias:          usb:v083ApA704d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p9018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p7010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1668p1200d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p7015d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3pB003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v040Dp3801d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04CAp4605d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3350d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3349d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3348d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3346d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3328d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3327d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3A10d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p9030d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p1006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p9271d*dc*dsc*dp*ic*isc*ip*
depends:        ath9k_hw,mac80211,ath9k_common,ath,cfg80211
vermagic:       2.6.38-11-generic SMP mod_unload modversions 686 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
``````
~$ sudo modinfo ath9k_htc
filename:       /lib/modules/**3.0.0-0300rc2-generic**/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
[B]firmware:       htc_9271.fw
firmware:       htc_7010.fw[/B]
description:    Atheros driver 802.11n HTC based wireless devices
license:        Dual BSD/GPL
author:         Atheros Communications
srcversion:     E38FCD3060996964BF650AD
alias:          usb:v0CF3p20FFd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA704d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p9018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p7010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1668p1200d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p7015d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3pB003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v040Dp3801d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04CAp4605d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3350d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3349d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3348d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3346d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3328d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3327d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3A10d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p9030d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p1006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p9271d*dc*dsc*dp*ic*isc*ip*
depends:        ath9k_hw,mac80211,ath9k_common,ath,cfg80211
vermagic:       3.0.0-0300rc2-generic SMP mod_unload modversions 686 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
```I am not offering this as a solution as there may be a easier/better one, but the 3.0 kernel does work with the newer firmware. As I stated I had the Natty 3.0 kernel before buying the USB adapter and getting it working was a snap.. 

These were the steps I did with the 3.0 kernel

Bought one
    Downloaded the driver installer
    [http://sourceforge.net/projects/ath9k-htc/files/ath9k_htc-installer/](http://sourceforge.net/projects/ath9k-htc/files/ath9k_htc-installer/)
    Execute the .deb packet
    Had already connected the WiFi adapter
    Needed the htc_9271.fw (firmware)
    Got it here [http://wireless.kernel.org/download/htc_fw/](http://wireless.kernel.org/download/htc_fw/)
    Moved it to /lib/firmware
* [COLOR=RoyalBlue]   Temporarily blacklisted my internal (b43) driver to stop any confusion[/COLOR]* (just my step)
    Rebooted It works my wireless only had g speeds

---

### Post by Robkg on 2011-08-29
> **nm_geo said:**
> I bought one of these just to do some testing, and I thought I had a very good solution to getting it going.  However, I had upgraded by Natty kernel to 3.0 just because I like to be on the so-called cutting edge.

Here is some pretty reviling information doing modinfo on the ath9k_htc in different Natty kernels.

```
~$ sudo modinfo ath9k_htc
filename:       /lib/modules/**2.6.38-11-generic/kernel/**drivers/net/wireless/ath/ath9k/ath9k_htc.ko
[B]firmware:       ar9271.fw
firmware:       ar7010_1_1.fw
firmware:       ar7010.fw[/B]
description:    Atheros driver 802.11n HTC based wireless devices
license:        Dual BSD/GPL
author:         Atheros Communications
srcversion:     8F244C9A8C97C1B3B163005
alias:          usb:v083ApA704d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p9018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p7010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1668p1200d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p7015d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3pB003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v040Dp3801d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04CAp4605d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3350d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3349d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3348d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3346d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3328d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3327d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3A10d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p9030d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p1006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p9271d*dc*dsc*dp*ic*isc*ip*
depends:        ath9k_hw,mac80211,ath9k_common,ath,cfg80211
vermagic:       2.6.38-11-generic SMP mod_unload modversions 686 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
``````
~$ sudo modinfo ath9k_htc
filename:       /lib/modules/**3.0.0-0300rc2-generic**/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
[B]firmware:       htc_9271.fw
firmware:       htc_7010.fw[/B]
description:    Atheros driver 802.11n HTC based wireless devices
license:        Dual BSD/GPL
author:         Atheros Communications
srcversion:     E38FCD3060996964BF650AD
alias:          usb:v0CF3p20FFd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA704d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p9018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p7010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1668p1200d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p7015d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3pB003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v040Dp3801d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04CAp4605d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3350d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3349d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3348d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3346d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3328d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3327d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3A10d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p9030d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p1006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p9271d*dc*dsc*dp*ic*isc*ip*
depends:        ath9k_hw,mac80211,ath9k_common,ath,cfg80211
vermagic:       3.0.0-0300rc2-generic SMP mod_unload modversions 686 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
```I am not offering this as a solution as there may be a easier/better one, but the 3.0 kernel does work with the newer firmware. As I stated I had the Natty 3.0 kernel before buying the USB adapter and getting it working was a snap.. 

These were the steps I did with the 3.0 kernel

Bought one
    Downloaded the driver installer
    [http://sourceforge.net/projects/ath9k-htc/files/ath9k_htc-installer/](http://sourceforge.net/projects/ath9k-htc/files/ath9k_htc-installer/)
    Execute the .deb packet
    Had already connected the WiFi adapter
    Needed the htc_9271.fw (firmware)
    Got it here [http://wireless.kernel.org/download/htc_fw/](http://wireless.kernel.org/download/htc_fw/)
    Moved it to /lib/firmware
* [COLOR=RoyalBlue]   Temporarily blacklisted my internal (b43) driver to stop any confusion[/COLOR]* (just my step)
    Rebooted It works my wireless only had g speeds

Can you explain it step by step, as I'm not experienced. Btw, I did some things already as written before. 

In the /lib/firmware folder I can find both the ar and the htc files, but I can't remove the ar files.

---

### Post by Robkg on 2011-08-29
I can see my network when using WiFi Radar, but I can't connect ;(

---

### Post by praseodym on 2011-08-29
Did you install the firmware as I posted above?

> ```
wget http://media.cdn.ubuntu-de.org/forum/attachments/2640681/ath_htc_firmware-1.tar.gz
sudo tar xvf ath_htc_firmware-1.tar.gz -C /lib/firmware
```

Just copy/paste the two lines into the terminal. This firmware is up-to-date. Reboot and control:

```
dmesg | egrep 'ath|firm'
iwconfig
lsmod
```

---

### Post by Robkg on 2011-08-29
> **praseodym said:**
> Did you install the firmware as I posted above?



Just copy/paste the two lines into the terminal. This firmware is up-to-date. Reboot and control:

```
dmesg | egrep 'ath|firm'
iwconfig
lsmod
```

```
dmesg | egrep 'ath|firm'
[    1.100550] device-mapper: multipath: version 1.2.0 loaded
[    1.100557] device-mapper: multipath round-robin: version 1.0.0 loaded
[   28.386168] intel_rng: don't want to disable this in firmware setup, and if
[   30.284991] usb 1-6: ath9k_htc: Transferred FW: ar9271.fw, size: 51312
[   30.550863] usb 1-6: ath9k_htc: HTC initialized with 33 credits
[   31.048757] ath: EEPROM regdomain: 0x60
[   31.048763] ath: EEPROM indicates we should expect a direct regpair map
[   31.048771] ath: Country alpha2 being used: 00
[   31.048775] ath: Regpair used: 0x60
[   31.067396] Registered led device: ath9k-phy0::radio
[   31.067462] Registered led device: ath9k-phy0::assoc
[   31.067557] Registered led device: ath9k-phy0::tx
[   31.067616] Registered led device: ath9k-phy0::rx
[   31.067624] usb 1-6: ath9k_htc: USB layer initialized
[   31.067683] usbcore: registered new interface driver ath9k_hif_usb

``````
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

``````
lsmod
Module                  Size  Used by
vesafb                 13449  1 
arc4                   12473  2 
snd_hda_codec_hdmi     27535  1 
snd_hda_intel          24113  0 
snd_hda_codec          90901  2 snd_hda_codec_hdmi,snd_hda_intel
binfmt_misc            13213  1 
snd_hwdep              13274  1 snd_hda_codec
snd_intel8x0           33213  1 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  5 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
ath9k_htc              55795  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
mac80211              257001  1 ath9k_htc
ppdev                  12849  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
fglrx                2434640  100 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
ath9k_common           13611  1 ath9k_htc
ath9k_hw              300328  2 ath9k_htc,ath9k_common
ath                    19141  2 ath9k_htc,ath9k_hw
cfg80211              156212  3 ath9k_htc,mac80211,ath
psmouse                73312  0 
parport_pc             32111  1 
snd                    55295  13 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                 17322  0 
soundcore              12600  1 snd
serio_raw              12990  0 
snd_page_alloc         14073  3 snd_hda_intel,snd_intel8x0,snd_pcm
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
hid_microsoft          12745  0 
usbhid                 41704  0 
hid                    77084  2 hid_microsoft,usbhid
usb_storage            43946  1 
uas                    17676  0 
tg3                   131476  0 
floppy                 60032  0 
```

---

### Post by BigD77 on 2011-08-29
> **walt.smith1960 said:**
> I don't know if you've tried this, it's worked for me with 10.04 &10.10.  Two stage process, first install the app then run the app found under applications > system tools.  The second process has to be run after each kernel (image) upgrade. I also didn't try anything else before running this software.  I don't know if trying other things first will cause problems with this app or not.

[http://sourceforge.net/projects/ath9k-htc/](http://sourceforge.net/projects/ath9k-htc/)

It also worked for me on a laptop with Ubuntu 9.10, and an old desktop with Lubuntu 11.04.   :popcorn:

---

### Post by praseodym on 2011-08-29
You may want to compile the newest driver by hand. To be sure uninstall the "ath9k_htc-installer" in synaptic, because I dont know if this tool is sticked to a single compat-wireless-package.

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
wget http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2        
tar jxvf compat-wireless-2.6.tar.bz2
cd compat-wireless-20*
./scripts/driver-select atheros 
make
sudo make install
```
and reboot. Check:

```
uname -a
iwconfig
sudo iwlist scan
dmesg | egrep 'ath|firm'
rfkill list
modinfo ath9k_htc
```
If it doesnt work we can install the kernel 3.0.

---

### Post by Robkg on 2011-08-29
> **praseodym said:**
> You may want to compile the newest driver by hand. To be sure uninstall the "ath9k_htc-installer" in synaptic, because I dont know if this tool is sticked to a single compat-wireless-package.

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
wget http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2        
tar jxvf compat-wireless-2.6.tar.bz2
cd compat-wireless-20*
./scripts/driver-select atheros 
make
sudo make install
```
and reboot. Check:

```
uname -a
iwconfig
sudo iwlist scan
dmesg | egrep 'ath|firm'
rfkill list
modinfo ath9k_htc
```
If it doesnt work we can install the kernel 3.0.

Half way I receive this message: 

```
tar jxvf compat-wireless-2.6.tar.bz2
bzip2: (stdin) is not a bzip2 file.
tar: Child returned status 2
tar: Error is not recoverable: exiting now

```

---

### Post by praseodym on 2011-08-29
Try to download by hand:

[http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)

put it in /home and try it again, starting with "tar". Maybe the download was incomplete.

---

### Post by Robkg on 2011-08-29
> **praseodym said:**
> Try to download by hand:

[http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)

put it in /home and try it again, starting with "tar". Maybe the download was incomplete.

I keep getting the same message...

I start to lose my patience a bit

---

### Post by praseodym on 2011-08-29
If I klick on that link, I can "open with archive manager" and it works. Now unpack the folder to /home and continue with the "cd"-command.

---

### Post by Robkg on 2011-08-30
> **praseodym said:**
> If I klick on that link, I can "open with archive manager" and it works. Now unpack the folder to /home and continue with the "cd"-command.

Thanks, this seems to work so far. These are the outputs that I get. Now how can I connect to my WiFi (it's the one called "WindmillCon")

```
:~$ uname -a
Linux robkg-HP-Compaq-dc7100-SFF-DX878AV 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:05:14 UTC 2011 i686 i686 i386 GNU/Linux

``````
:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

``````
:~$ sudo iwlist scan
[sudo] password for robkg: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:22:3F:8C:C9:38
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"WindmillCon"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000002f2d51c
                    Extra: Last beacon: 1052ms ago
                    IE: Unknown: 000B57696E646D696C6C436F6E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3402001900000000000000000000000000000000000000
                    IE: Unknown: 3D1602001900000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: DD820050F204104A000110104400010210570001001041000100103B00010310470010565AA94967C14C0EAA8FF349E6F593111021000D4E6574676561722C20496E632E10230007574E523230303010240007574E523230303010420004353637381054000800060050F204000110110007574E5232303030100800020084103C000103
          Cell 02 - Address: 00:24:B2:8B:29:EC
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key:on
                    ESSID:"NETGEARJB"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000055b68a5e9c
                    Extra: Last beacon: 504ms ago
                    IE: Unknown: 00094E4554474541524A42
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F0000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: 00:13:10:0A:F1:E6
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"estelleo"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000038d518bdc02
                    Extra: Last beacon: 976ms ago
                    IE: Unknown: 0008657374656C6C656F
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030103
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020204
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

``````

MY PC:~$ dmesg | egrep 'ath|firm'
[    1.092533] device-mapper: multipath: version 1.2.0 loaded
[    1.092540] device-mapper: multipath round-robin: version 1.0.0 loaded
[   20.822425] intel_rng: don't want to disable this in firmware setup, and if
[   23.472523] usb 1-6: ath9k_htc: Transferred FW: htc_9271.fw, size: 51272
[   23.707511] ath9k_htc 1-6:1.0: ath9k_htc: HTC initialized with 33 credits
[   23.902646] ath9k_htc 1-6:1.0: ath9k_htc: FW Version: 1.3
[   23.902653] ath: EEPROM regdomain: 0x60
[   23.902657] ath: EEPROM indicates we should expect a direct regpair map
[   23.902663] ath: Country alpha2 being used: 00
[   23.902668] ath: Regpair used: 0x60
[   23.916634] Registered led device: ath9k_htc-phy0
[   23.916644] usb 1-6: ath9k_htc: USB layer initialized
[   23.917663] usbcore: registered new interface driver ath9k_htc

``````
:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

``````
:~$ modinfo ath9k_htc
filename:       /lib/modules/2.6.38-11-generic/updates/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
firmware:       htc_9271.fw
firmware:       htc_7010.fw
description:    Atheros driver 802.11n HTC based wireless devices
license:        Dual BSD/GPL
author:         Atheros Communications
srcversion:     20E12587B7F0F963C46A385
alias:          usb:v0CF3p20FFd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p017Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA704d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p9018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p7010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1668p1200d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p7015d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3pB003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v040Dp3801d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04CAp4605d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3350d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3349d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3348d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3346d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3328d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3327d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3A10d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p9030d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p1006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p9271d*dc*dsc*dp*ic*isc*ip*
depends:        ath9k_hw,ath9k_common,mac80211,ath,cfg80211
vermagic:       2.6.38-11-generic SMP mod_unload modversions 686 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)


```

---

### Post by wildmanne39 on 2011-08-30
Hi, make sure your router is set to wpa2 only not mixed mode if that does not work do this please.
```
sudo ifconfig wlan0 down
sudo rmmod -f ath9k
sudo modprobe ath9k nohwcrypt=1
sudo ifconfig wlan0 up
```
make sure your wired connection is disconnected first.
Thank you

---

### Post by Robkg on 2011-08-30
Which code do I use to connect to the wifi?

---

### Post by wildmanne39 on 2011-08-30
Hi, run each of those codes as listed one at a time and you should be able to connect after the last one completes.
Thank you

---

### Post by Robkg on 2011-08-30
> **wildmanne39 said:**
> Hi, run each of those codes as listed one at a time and you should be able to connect after the last one completes.
Thank you

I'm stupid, I know, but how do I make the connection?

---

### Post by wildmanne39 on 2011-08-30
Hi, in the top right corner of the screen click on the internet icon make sure wireless is enabled, also you should see the connection you want to connect too.

You will have to enter your wireless key for your router.
Thank you

---

### Post by Robkg on 2011-08-30
> **wildmanne39 said:**
> Hi, in the top right corner of the screen click on the internet icon make sure wireless is enabled, also you should see the connection you want to connect too.

You will have to enter your wireless key for your router.
Thank you
I don't have any icon there? Should I install something?

---

### Post by wildmanne39 on 2011-08-30
Hi, if it is there it should be next to the speaker if you do not see it run this command, it will tell if network manger is running.
```
ps aux | grep nm-apple
```
if not you can install it from synaptic by typing in network manager in the search box in synaptic then put a check by network manager and click apply.
Thank you

---

### Post by Robkg on 2011-08-30
YES IT WORKS! :D THANK YOU! 

Both of you! Can I praise you somewhere? :D

---

### Post by wildmanne39 on 2011-08-30
Hi, I am glad you have it working, praseodym is great with these issues, would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

### Post by Robkg on 2011-08-30
> **Robkg said:**
> YES IT WORKS! :D THANK YOU! 

Both of you! Can I praise you somewhere? :D

Okay, one slight problem, when I close the terminal, the indicator disappears and the connection gets lost

I posted this issue here: [http://ubuntuforums.org/showthread.php?p=11203276#post11203276](http://ubuntuforums.org/showthread.php?p=11203276#post11203276)

---

### Post by wildmanne39 on 2011-08-30
Hi, is this the command that activated network manager?
```
ps aux | grep nm-apple
```
Thank you

---

