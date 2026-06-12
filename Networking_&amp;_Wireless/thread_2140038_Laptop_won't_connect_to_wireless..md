---
title: "Laptop won't connect to wireless."
date: 2013-04-28
forum: Networking &amp; Wireless
---

### Post by rdp1408 on 2013-04-28
Hello, I have a Asus G75VW laptop that dual boots Windows 7 and Ubuntu 12.04. It has an Atheros AR9485 wireless card in it. I can see my WiFi but when I try to connect to it it tries it for a minute, then asks for the password, and then repeats indefinitely. I've pasted some output that is commonly asked for in other threads. I also tried to disable the hardware encryption (recommended in another thread) but that didn't solve anything.

rfkill list all:
```

1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: asus-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no

```

nmcli nm satus:
```

RUNNING         STATE           WIFI-HARDWARE   WIFI       WWAN-HARDWARE   WWAN      
running         connected       enabled         enabled    enabled         disabled 

```

lsmod:
```

Module                  Size  Used by
vesafb                 13844  1 
joydev                 17693  0 
snd_hda_codec_hdmi     32474  4 
asus_nb_wmi            12710  0 
asus_wmi               24456  1 asus_nb_wmi
sparse_keymap          13890  1 asus_wmi
nvidia              11308613  42 
snd_hda_codec_via      51474  1 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd_seq_midi           13324  0 
rfcomm                 47604  0 
video                  19651  0 
bnep                   18281  2 
snd_hda_intel          33719  5 
arc4                   12529  2 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
snd_rawmidi            30748  1 snd_seq_midi
parport_pc             32866  0 
ath9k                 132428  0 
mac80211              506862  1 ath9k
ppdev                  17113  0 
wmi                    19256  1 asus_wmi
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
ath9k_common           14053  1 ath9k
ath9k_hw              411239  2 ath9k,ath9k_common
snd_seq_midi_event     14899  1 snd_seq_midi
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
mac_hid                13253  0 
psmouse                97485  0 
cfg80211              205774  3 ath9k,mac80211,ath
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
ath3k                  12961  0 
btusb                  18332  0 
bluetooth             180153  12 rfcomm,bnep,ath3k,btusb
serio_raw              13211  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_timer              29990  2 snd_pcm,snd_seq
snd                    79041  20 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_seq_device,snd_timer
mei                    41616  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
atl1c                  41718  0

```

---

### Post by praseodym on 2013-04-28
Deactivate the hardware encryption of the driver:
```

echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```

---

### Post by rdp1408 on 2013-04-28
I did disable the hardware encryption. I mentioned that in the original post.

---

### Post by CrackedP0t on 2013-04-28
Try moving the laptop closer to the router, with a clear line of sight.

---

### Post by praseodym on 2013-04-28
Ok, sorry. Please check:
```

route -n
cat /etc/resolv.conf
sudo iwlist scan
iwconfig
ifconfig -a
```

---

