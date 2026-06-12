---
title: "MAJOR wireless woes"
date: 2012-12-30
forum: Networking &amp; Wireless
---

### Post by karnival8 on 2012-12-30
I am very new to Linux. 

I have a laptop, a Lenovo Yoga 13 which is awesome. 

I decided I wanted to run the latest Ubuntu and get back into it. 

This machine comes with a built-in Realtek RTL8723A adapter. 

After spending a while looking around and trying some obscure modules it seemed as if this built-in card is too new and is just not supported. Bummer. 

So, I got a Netgear WNA1000M USB adapter. 

Well, I've been messing with this one for about 3 days now. I have been using the help of this forum post:
[http://ubuntuforums.org/showthread.php?t=1806839]("http://ubuntuforums.org/showthread.php?t=1806839")

The above forum helped me to get it up and running HOWEVER; the connection is SUPER unreliable. It will stay connected for about 5 minutes, if at all. Then after a series of reboots and unplugging the hardware I may have a small shot of it working again for another few minutes. 

Here are some symptoms:
If I do get a connection, the signal strength is about 75% when the machine is 1 foot away from the router, from the other room it just craps out. 
Sometimes it finds the other wireless networks in the neighborhood, sometimes not. No matter what, the list is never the same like is on my windows machines. 
When it's not working, and I attempt to connect to my stored network, it just keeps asking me for the wireless key even when entered correctly and then it never connects but keeps asking me to enter the key again. 

The best case here is if we can get the onboard RTL8723 to work, that would be amazing. 

If not, it would be really great to get this USB adapter working. 

Go easy on me, I am VERY new to Linux.


Dumps are:
lwconfig
```
wlan0     Link encap:Ethernet  HWaddr 84:1b:5e:97:7b:6f 
          inet6 addr: fe80::861b:5eff:fe97:7b6f/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2599 (2.5 KB)  TX bytes:3611 (3.6 KB)
```

lsmod
```
Module                  Size  Used by
uvcvideo               71277  0
videobuf2_core         32070  1 uvcvideo
videodev               95841  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12756  1 uvcvideo
videobuf2_memops       13184  1 videobuf2_vmalloc
hid_generic            12445  0
snd_hda_codec_hdmi     31423  1
snd_hda_codec_conexant    52202  1
hid_multitouch         13007  0
usbhid                 41702  1 hid_multitouch
hid                    82142  3 hid_generic,hid_multitouch,usbhid
joydev                 17161  0
bnep                   17707  2
rfcomm                 37276  0
bluetooth             183228  10 bnep,rfcomm
parport_pc             31968  0
ppdev                  12817  0
rts5139               281367  0
arc4                   12473  2
rtl8192cu              66592  0
rtl8192c_common        46967  1 rtl8192cu
rtlwifi                68911  1 rtl8192cu
mac80211              512815  3 rtl8192cu,rtl8192c_common,rtlwifi
cfg80211              440879  2 rtlwifi,mac80211
coretemp               13168  0
snd_hda_intel          32515  3
snd_hda_codec         111547  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
kvm                   357806  0
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80163  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0
snd_rawmidi            25382  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
aesni_intel            17938  0
cryptd                 15614  1 aesni_intel
aes_i586               16956  1 aesni_intel
i915                  531079  3
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
microcode              18209  0
drm_kms_helper         47545  1 i915
ideapad_laptop         13670  0
wmi                    18590  0
snd_timer              24411  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    61991  16 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   227424  4 i915,drm_kms_helper
sparse_keymap          13658  1 ideapad_laptop
psmouse                84843  0
i2c_algo_bit           13197  1 i915
serio_raw              13031  0
mac_hid                13037  0
compat                 18863  6 rtl8192cu,rtlwifi,mac80211,cfg80211,i915,drm
soundcore              14599  1 snd
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
mei                    35796  0
Module                  Size  Used by
uvcvideo               71277  0
videobuf2_core         32070  1 uvcvideo
videodev               95841  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12756  1 uvcvideo
videobuf2_memops       13184  1 videobuf2_vmalloc
hid_generic            12445  0
snd_hda_codec_hdmi     31423  1
snd_hda_codec_conexant    52202  1
hid_multitouch         13007  0
usbhid                 41702  1 hid_multitouch
hid                    82142  3 hid_generic,hid_multitouch,usbhid
joydev                 17161  0
bnep                   17707  2
rfcomm                 37276  0
bluetooth             183228  10 bnep,rfcomm
parport_pc             31968  0
ppdev                  12817  0
rts5139               281367  0
arc4                   12473  2
rtl8192cu              66592  0
rtl8192c_common        46967  1 rtl8192cu
rtlwifi                68911  1 rtl8192cu
mac80211              512815  3 rtl8192cu,rtl8192c_common,rtlwifi
cfg80211              440879  2 rtlwifi,mac80211
coretemp               13168  0
snd_hda_intel          32515  3
snd_hda_codec         111547  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
kvm                   357806  0
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80163  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0
snd_rawmidi            25382  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
aesni_intel            17938  0
cryptd                 15614  1 aesni_intel
aes_i586               16956  1 aesni_intel
i915                  531079  3
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
microcode              18209  0
drm_kms_helper         47545  1 i915
ideapad_laptop         13670  0
wmi                    18590  0
snd_timer              24411  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    61991  16 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   227424  4 i915,drm_kms_helper
sparse_keymap          13658  1 ideapad_laptop
psmouse                84843  0
i2c_algo_bit           13197  1 i915
serio_raw              13031  0
mac_hid                13037  0
compat                 18863  6 rtl8192cu,rtlwifi,mac80211,cfg80211,i915,drm
soundcore              14599  1 snd
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
mei                    35796  0 
```


lsusb
```
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 0846:9041 NetGear, Inc. WNA1000M 802.11bgn [Realtek RTL8188CUS]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp.
Bus 001 Device 004: ID 0bda:1724 Realtek Semiconductor Corp.
Bus 001 Device 005: ID 04f3:000a Elan Microelectronics Corp.
Bus 002 Device 003: ID 2047:0855 Texas Instruments
Bus 002 Device 004: ID 04f2:b322 Chicony Electronics Co., Ltd
			
```

---

### Post by Pjotr123 on 2012-12-30
Have you already tried disabling power management for the wireless card? Can be done like this:
[https://sites.google.com/site/easylinuxtipsproject/internet#TOC-Disable-power-management-for-the-wireless-card](https://sites.google.com/site/easylinuxtipsproject/internet#TOC-Disable-power-management-for-the-wireless-card)
(item 2.1, right column)

---

### Post by chili555 on 2012-12-30
> This machine comes with a built-in Realtek RTL8723A adapter.

After spending a while looking around and trying some obscure modules it seemed as if this built-in card is too new and is just not supported. Bummer.
Ahh, but it is. If I were you, I'd give the USB to the desk drawer and install the driver *_and the firmware_* as here: [http://ubuntuforums.org/showthread.php?t=2098755&highlight=8723](http://ubuntuforums.org/showthread.php?t=2098755&highlight=8723)

The part lots of people seem to miss is the firmware mentioned at post #21.

---

### Post by karnival8 on 2012-12-30
i have continued this post and errors i'm getting here:
[http://ubuntuforums.org/showthread.php?p=12429301](http://ubuntuforums.org/showthread.php?p=12429301)

---

