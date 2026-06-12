---
title: "rt5370 usb wireless cannot shutdown &amp; restart normally"
date: 2012-05-12
forum: Networking &amp; Wireless
---

### Post by gaoyuhui on 2012-05-12
Hi, guys
I have newly installed 12.04 & then installed my usb wireless, It works. But then, I can't shutdown & restart my computer normally. It will stuck in the UBUNTU Interface. But, After removing USB wireless before shutdown, the problem Disappears. So, it must be the USB wireless' problem.

Follows:
the USB install:
1&#65306;drive:2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO downloaded from RT web.
2:find os/linux/config.mk & set  HAS_WPA_SUPPLICANT=y
  HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
3:find os/linux/usb_main_dev.c & add
  MODULE_LICENSE("GPL");
4: make & make install
5: find /etc/modprobe.d/blacklist.conf
  & add 
  blacklist rt2x00lib
  blacklist rt2x00usb
  blacklist rt2500usb
  blacklist rt2800usb
6:find /etc/modules & set
  rt5370sta
7:sudo modprobe rt3070sta in terminal
After this, my wireless works, but the problem follows simultaneously.

the lsmod information:
Module                  Size  Used by
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
snd_hda_codec_analog    75395  1 
snd_hda_intel          32765  2 
snd_hda_codec         109562  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
ppdev                  12849  0 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
snd_seq_midi           13132  0 
dcdbas                 14098  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
psmouse                72846  0 
parport_pc             32114  1 
serio_raw              13027  0 
wmi                    18744  1 dell_wmi
mac_hid                13077  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
rt5370sta             726167  1 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  13 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
i915                  414603  3 
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
usbhid                 41906  0 
hid                    77367  1 usbhid
e1000e                140005  0 

Does anybd experience this? And how can't I fix this?
Thx!

---

