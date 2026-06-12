---
title: "Wireless dell inspiron b130 lubuntu"
date: 2012-05-07
forum: Networking &amp; Wireless
---

### Post by bezekuma on 2012-05-07
Hello, I am quite new to linux and have only had experience with basic use in ubuntu. Recently I came into possession of an old dell inspiron b130. Windows did not run very well at all, and I wanted to gain more experience using linux, so I installed Lubuntu 12.04 on the machine and so far it has worked great except for one problem: the wireless card is not working. As far as I can tell, it isn't registering that it even exists. I ran iwconfig and this is the result:
```
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions
```.
I'm assuming this means it doesn't think I have a card.
Any help would be greatly appreciated.

---

### Post by praseodym on 2012-05-07
Hi,

looks like the card is turned off? Any button/switch/keys/key combinations? Please show:

```
lspci -nnk | grep -iA2 net
rfkill list
lsmod
```

---

### Post by chili555 on 2012-05-07
> I'm assuming this means it doesn't think I have a card.It means that it thinks you *do* have a card, but it's not associated with any access point yet; that is, not connected.> wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  [COLOR="Red"]Access Point: Not-Associated[/COLOR]   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:onWhen you click the Network Manager icon, do you see your network? How about letting us see the usual suspects:```
rfkill list all
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by bezekuma on 2012-05-07
To Praseodym:

```
main@ubuntumaderine:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
	Subsystem: Dell Device [1028:01c9]
	Kernel driver in use: b44
--
02:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
	Subsystem: Dell Wireless 1370 WLAN Mini-PCI Card [1028:0005]
	Kernel driver in use: b43-pci-bridge
main@ubuntumaderine:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
main@ubuntumaderine:~$ lsmod
Module                  Size  Used by
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
arc4                   12473  2 
snd_hda_codec_idt      60251  1 
snd_hda_intel          32765  1 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
b43                   342643  0 
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
mac80211              436455  1 b43
snd_seq_midi_event     14475  1 snd_seq_midi
cfg80211              178679  2 b43,mac80211
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                 17393  0 
i915                  414568  2 
snd                    62064  11 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
drm_kms_helper         45466  1 i915
bcma                   25651  1 b43
drm                   197692  3 i915,drm_kms_helper
psmouse                87213  0 
dell_laptop            13671  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
serio_raw              13027  0 
dcdbas                 14098  1 dell_laptop
mac_hid                13077  0 
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
b44                    31412  0 
ssb                    50691  2 b43,b44
```


To chili:
When I click the network icon, under wireless networks it says device not read (firmware missing).
That command returns:

```
main@ubuntumaderine:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
main@ubuntumaderine:~$ lspci -nn | grep 0280
02:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
```

I don't think There are any switches turned off because in the short time I was using it with windows the wireless worked perfectly.

---

### Post by chili555 on 2012-05-07
Please hook up the ethernet temporarily and do:```
sudo apt-get install linux-firmware-nonfree
sudo modprobe -r b43
sudo modprobe b43
```Detach the ethernet and tell us if it's working as expected.

---

### Post by bezekuma on 2012-05-07
Thank you so much chili! It's working fine now :D

---

### Post by chili555 on 2012-05-07
Awesome! Please use thread tools at the top to Mark Solved.

Have fun!

---

