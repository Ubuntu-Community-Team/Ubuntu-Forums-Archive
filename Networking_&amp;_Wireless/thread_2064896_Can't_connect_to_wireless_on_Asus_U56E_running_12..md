---
title: "Can't connect to wireless on Asus U56E running 12.04"
date: 2012-09-30
forum: Networking &amp; Wireless
---

### Post by NARtardd on 2012-09-30
Hi everybody,

First I would like to say that I am brand new to Ubuntu and Linux in general. I've wanted to give it a try for a while now, and finally decided to hop right in. After install, everything was fine except that I couldn't connect via wireless. My OS detects my wireless card, and can see my SSID, but upon entering my password it just seems to never connect and constantly asking for my credentials every few minutes and repeats the process. Even if I'm connected via wired (which works perfect).

Apparently this is a common issue? I'm just not sure if solutions are specific to different wireless cards/laptops.

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
Linux stephen-U56E 3.2.0-31-generic #50-Ubuntu SMP Fri Sep 7 16:16:45 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
``````
02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N + WiMAX 6150 [8086:0885] (rev 67)
    Subsystem: Intel Corporation Centrino Wireless-N + WiMAX 6150 BGN [8086:1305]
    Kernel driver in use: iwlwifi
--
04:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1851]
    Kernel driver in use: atl1c

``````
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 8087:07d6 Intel Corp. 
Bus 001 Device 004: ID 13d3:5710 IMC Networks 
Bus 003 Device 002: ID 1532:0017 Razer USA, Ltd Imperator Mouse
``````
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.
``````
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-wimax: WiMAX
    Soft blocked: yes
    Hard blocked: no
``````
Module                  Size  Used by
usbhid                 47199  0 
hid                    99559  1 usbhid
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   224173  1 
joydev                 17693  0 
arc4                   12529  2 
asus_nb_wmi            12710  0 
asus_wmi               24456  1 asus_nb_wmi
sparse_keymap          13890  1 asus_wmi
rfcomm                 47604  0 
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
snd_seq_midi           13324  0 
v4l2_compat_ioctl32    17128  1 videodev
snd_rawmidi            30748  1 snd_seq_midi
psmouse                97362  0 
serio_raw              13211  0 
snd_seq_midi_event     14899  1 snd_seq_midi
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
parport_pc             32866  0 
ppdev                  17113  0 
iwlwifi               396989  0 
mac80211              506816  1 iwlwifi
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  473240  3 
cfg80211              205544  2 iwlwifi,mac80211
mac_hid                13253  0 
wmi                    19256  1 asus_wmi
drm_kms_helper         46978  1 i915
drm                   242038  4 i915,drm_kms_helper
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41616  0 
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
atl1c                  41718  0 
```Thanks in advance. I know with all of your help, I'll get this issue solved!

Edit: I notice under iwconfig it states: WiMax, Softblock: yes. Can anyone explain what that means?

---

### Post by uncaspi on 2012-09-30
This could be many things, but have you tried to unsecure your network????

I dont know what wimax softblocked means.

---

### Post by NARtardd on 2012-09-30
> **uncaspi said:**
> This could be many things, but have you tried to unsecure your network????

I dont know what wimax softblocked means.

Unsecure as in my SSID not needing a password? No. I have not tried that.

---

### Post by uncaspi on 2012-09-30
No password to determine if it has something to do with the authentification.

---

