---
title: "snd-hda-intel: merging headphone and front volume controls"
date: 2006-06-22
forum: Multimedia &amp; Video
---

### Post by Cisto on 2006-06-22
I have a Asus a6va laptop equipped with a Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04). In order to get headphone jack working, I had to put in /etc/modprobe.d/alsa-base "options snd-hda-intel model=z71v position_fix=1". Anyway I'm having problems with the laptop's multimedia keys: by default, the XF86AudioMute, XF86RaiseVolume and XF86LowerVolume are changing just the headphone volume, which is not very useful. I know that with intel 8x0 soundcards it is possible to merge headphone and front audio vulume controls by modprobing the 8x0 module with ac97_quirk=hponly. Now my question is: how can I do something similar with the snd-hda-intel module? Modinfo didn't gave me anything similar to this option.

Thank you much.

---

### Post by Cylence on 2006-06-22
Thank you Cisto, I finally got the headphones working! That was my major turnoff.

I'd be glad too if anyone comes up with a solution for managing the main volume using multimedia keys. Although I connect my laptop to external speakers most of the time, this problem is a hassle when using the in-built speakers.

---

### Post by lazyron on 2006-07-08
Just wanted to bump this post because it worked on my Dell e1405.

> lspci
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

> lsmod | grep snd
snd_hda_intel          20468  1
snd_hda_codec         151056  1 snd_hda_intel
snd_pcm_oss            56448  0
snd_mixer_oss          20544  1 snd_pcm_oss
snd_pcm                96708  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              26884  1 snd_pcm
snd                    60004  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10784  1 snd
snd_page_alloc         11304  2 snd_hda_intel,snd_pcm

---

### Post by nobodysdarling on 2006-07-09
Wonder if this would work for my Vaio. I can control HDA with mulitmedia key's , but when I have external speaker's plugged in , I cannot get any volume control , except from the app's own Volume control

---

