---
title: "Issues With &quot;hp-wifi&quot; And &quot;rfkill&quot; - URGENT!"
date: 2011-10-15
forum: Networking &amp; Wireless
---

### Post by AdamShumpisxXx on 2011-10-15
My issue is that EVERY TIME I boot the laptop I have to hit the physical button and run:

```
rfkill unblock wifi
```

...to get on my wireless network. It works fine after that but this laptop has to go back to my best friend's father TODAY and he's not going to tolerate that. This issue never happened in Ubuntu 9.04 but now this is not an option. Is there some way to automate this process at startup? Thank you in advance for your help!

---

### Post by wildmanne39 on 2011-10-15
Hi, please show:
```
lsmod
```
Thank you

---

### Post by AdamShumpisxXx on 2011-10-15
Sorry about the delay. I got frustrated so I shut down the laptop and went to the range. Oddly enough when I got back and powered it back on it auto-connected to my wireless network! The button goes from blue to red sometimes randomly but everything seems fine. I don't want this to be something that reoccurs though. Here is the output of that command:

```
USER@COMPUTER:~$ lsmod
Module                  Size  Used by
cryptd                 19801  0 
aes_i586               16956  1 
aes_generic            38023  1 aes_i586
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     27479  1 
snd_hda_codec_conexant    43782  1 
joydev                 17322  0 
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
arc4                   12473  2 
snd_seq_midi           13132  0 
i915                  450944  3 
ath5k                 144412  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ath                    19141  1 ath5k
mac80211              257001  1 ath5k
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
hp_wmi                 13418  0 
binfmt_misc            13213  1 
sparse_keymap          13666  1 hp_wmi
snd_timer              28659  2 snd_pcm,snd_seq
drm_kms_helper         40745  1 i915
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   180037  4 i915,drm_kms_helper
cfg80211              156212  3 ath5k,ath,mac80211
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
serio_raw              12990  0 
soundcore              12600  1 snd
i2c_algo_bit           13184  1 i915
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  3 
r8169                  42534  0 
libahci                25548  1 ahci

```

---

### Post by wildmanne39 on 2011-10-15
Hi, 
Please do:
```
gksudo gedit /etc/rc.local
```
Add your three lines above exit 0
```
rmmod -f ath5k
rfkill unblock all
modprobe ath5k
```
Proofread carefully, save and close gedit. Reboot and tell us if it's working as expected.
Thank you

---

