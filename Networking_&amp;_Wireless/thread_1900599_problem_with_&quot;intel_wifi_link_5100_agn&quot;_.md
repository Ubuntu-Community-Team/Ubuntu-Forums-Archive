---
title: "problem with &quot;intel wifi link 5100 agn&quot; on &quot;11.10&quot;"
date: 2011-12-26
forum: Networking &amp; Wireless
---

### Post by Pater Puff on 2011-12-26
HI there!

I have just installed Ubuntu 11.10 as my 2. partition on my Lenovo U550 ideapad (next to windows 7) and I would, naturaly, like to connect my computer to the WIFI. My first thought is that it is the driver that is not functioning, as it can't unblock the Wireless LAN.


I have tryed to do a ```
rfkill list all 
``` in the terminal, and the output was:
```
3. acer-wireless: wireless LAN
Soft blocked: yes
Hard blocked: no
```

I have also tryed to unblock it as described in this guide (mostly in Danish, sorry): [http://www.freedomnotbeer.dk/index.php?option=com_content&view=article&id=98&Itemid=102#20](http://www.freedomnotbeer.dk/index.php?option=com_content&view=article&id=98&Itemid=102#20)

But this didn't seem to work. I have unfortunately damaged the cable port to the ethernet cable, and therefore i am working with moving files and drivers by my eksternal harddisk.

I have tried to download the driver ```
iwlwifi-5000-5.ucode 
``` and toss it in the folder called ```
lib/firmware
``` but it wouldn't let me.



my card is btw. Intel wifi link 5100 agn
My computer is a Lenovo U550

Any ideas please?

---

### Post by westie457 on 2011-12-26
Hi could you post the output of ```
lsmod
``` please

---

### Post by Pater Puff on 2011-12-26
```
Module                  Size  Used by 
bnep                   18436  2 
rfcomm                 47946  8 
parport_pc             36962  0 
ppdev                  17113  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
joydev                 17693  0 
binfmt_misc            17540  1 
arc4                   12529  2 
acer_wmi               23948  0 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi 
snd_hda_intel          33390  3 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel 
snd_hwdep              13668  1 snd_hda_codec 
uvcvideo               72711  0 
videodev               93004  1 uvcvideo 
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec 
v4l2_compat_ioctl32    17083  1 videodev 
snd_seq_midi_event     14899  1 snd_seq_midi 
radeon               1015995  0 
i915                  566711  3 
iwlagn                314213  0 
mac80211              310872  1 iwlagn 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event 
btusb                  18600  2 
psmouse                73882  0 
bluetooth             166112  23 bnep,rfcomm,btusb 
snd_timer              29991  2 snd_pcm,snd_seq 
ttm                    76805  1 radeon 
serio_raw              13166  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq 
drm_kms_helper         42558  2 radeon,i915 
cfg80211              199587  2 iwlagn,mac80211 
drm                   236330  6 radeon,i915,ttm,drm_kms_helper 
snd                    68266  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_rawmidi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_seq_device 
ideapad_laptop         13871  0 
sparse_keymap          13890  2 acer_wmi,ideapad_laptop 
i2c_algo_bit           13423  2 radeon,i915 
soundcore              12680  1 snd 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm 
video                  19412  1 i915 
wmi                    19256  1 acer_wmi 
ahci                   26002  1 
libahci                26861  1 ahci 
atl1c                  41643  0 
```

---

### Post by westie457 on 2011-12-26
Take a look at this thread [http://ubuntuforums.org/showthread.php?t=1894160](http://ubuntuforums.org/showthread.php?t=1894160)
Try the suggestions in the first post, if that works do the suggestion in the second post.

If it does not work post any error messages and we will try something else.

---

### Post by Pater Puff on 2011-12-26
Thank you very much, it worked like a charm!

---

### Post by westie457 on 2011-12-26
> **Pater Puff said:**
> Thank you very much, it worked like a charm!

Great, glad it worked. Could you mark this as 'Solved' please using 'Thread Tools' at the top of the page.

Thank you.

---

