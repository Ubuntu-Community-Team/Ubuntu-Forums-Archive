---
title: "Wireless not worling after trying to patch the driver BCM4312 or RT73"
date: 2012-06-17
forum: Networking &amp; Wireless
---

### Post by Amanuntu on 2012-06-17
While trying to patch the driver for my Linksys USB wireless adapter WUSB54GC V1 i lost my wireless connectivity. It not only effected my usb adapter but also my inbuilt Broadcom BCM4312 adapter that has STA wireless driver already activated.

Under network menu, for wireless it say """wireless is disabled by hardware switch"" however my physical wireless switch is on.

My laptop is E6500

---

### Post by wildmanne39 on 2012-06-17
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

### Post by Amanuntu on 2012-06-18
cat /etc/lsb-release; uname -a
```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux admin2636-Latitude-E6500 3.2.0-25-generic-pae #40-Ubuntu SMP Wed May 23 22:11:24 UTC 2012 i686 i686 i386 GNU/Linux

```

```

00:19.0 Ethernet controller [0200]: Intel Corporation 82567LM Gigabit Network Connection [8086:10f5] (rev 03)
    Subsystem: Dell Device [1028:024f]
    Kernel driver in use: e1000e
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
    Kernel driver in use: wl

```

```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0c45:63f8 Microdia Sonix Integrated Webcam
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 005 Device 002: ID 0a5c:5800 Broadcom Corp. BCM5880 Secure Applications Processor
Bus 006 Device 002: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 003 Device 003: ID 413c:8157 Dell Computer Corp. Integrated Keyboard
Bus 003 Device 004: ID 413c:8158 Dell Computer Corp. Integrated Touchpad / Trackstick
Bus 003 Device 005: ID 413c:8156 Dell Computer Corp. Wireless 370 Bluetooth Mini-card
Bus 002 Device 003: ID 13b1:0020 Linksys WUSB54GC v1 802.11g Adapter [Ralink RT73]

```

```

lo        no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:199
          Rx invalid nwid:0  invalid crypt:527  invalid misc:0

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.


```


```

0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
4: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

```
Module                  Size  Used by
rt73usb                27029  0 
crc_itu_t              12627  1 rt73usb
rt2x00usb              20061  1 rt73usb
rt2x00lib              48858  2 rt73usb,rt2x00usb
mac80211              436455  2 rt2x00usb,rt2x00lib
cfg80211              178679  2 rt2x00lib,mac80211
michael_mic            12540  4 
arc4                   12473  4 
parport_pc             32114  0 
bnep                   17830  2 
rfcomm                 38139  12 
ppdev                  12849  0 
btusb                  17912  2 
bluetooth             158438  23 bnep,rfcomm,btusb
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_idt      60251  1 
lib80211_crypt_tkip    17275  0 
wl                   2646601  0 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
joydev                 17393  0 
dell_laptop            17767  0 
dcdbas                 14098  1 dell_laptop
snd_hda_intel          32765  3 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
lib80211               14040  2 lib80211_crypt_tkip,wl
mac_hid                13077  0 
snd_hwdep              13276  1 snd_hda_codec
wmi                    18744  1 dell_wmi
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
psmouse                72919  0 
serio_raw              13027  0 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
usbhid                 41906  0 
hid                    77367  1 usbhid
i915                  414663  4 
drm_kms_helper         45466  1 i915
drm                   197692  5 i915,drm_kms_helper
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
uvcvideo               67203  0 
i2c_algo_bit           13199  1 i915
videodev               86588  1 uvcvideo
video                  19068  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
e1000e                140005  0 

```


Thanks

---

### Post by wildmanne39 on 2012-06-18
Hi, try this:
```
sudo rmmod -f dell-laptop
```
make sure your physical switch is on then run:
```
rfkill list all
```
and make sure it does not say soft or hard blocked.

I have never seen a wireless usb adapter and an internal card that can be used at the same time so unplug your usb adapter before running the commands.
Thanks

---

