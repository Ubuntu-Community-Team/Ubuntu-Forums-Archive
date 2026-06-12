---
title: "Problems with realtek and 5.1 sound"
date: 2007-04-11
forum: Multimedia &amp; Video
---

### Post by MrNobody on 2007-04-11
Hi,
i have a new PC with a HDA Nvidia audio card with chip Realtek ALC861
There's sound, but only in stereo, using alsa 1.0.13
I've downloaded drivers from realtek web (especially designed for these chips, based on alsa 1.0.12, to get 5.1 sound) but same stereo output as with alsa 1.0.13.
My last test was using alsa 1.0.14-r3, and alsamixer looked a bit different (i could enable digital audio from here), but no way with 5.1
I don't know what else i can do, any idea?, tired of getting nothing... :( 

Thanks in advance

---

### Post by MrNobody on 2007-04-12
When installing new alsa drivers (realtek drivers based on alsa, or alsa-1.0.14rc3), there's a step in installation that don´t know how to do and if, maybe, is part of my problem:

**Step 2. Turn on sound support (soundcore module, default turn on)**

Should i do anything to enable sound support?
When "make install" for alsa-driver (realtek or 1.0.14rc3), soundcore.ko is not reinstalled (not copied to /etc/modules/.../kernel/sound/), and the system always loads soundcore.ko that came originally with ubuntu (alsa-1.0.13 if i'm right, with Ubuntu 6.10).

I can see that, as part of realtek driver, there's a sound_core.c (realtek-linux-audiopack-4.05f\alsa-driver-1.0.12-4.05f\alsa-kernel\sound_core.c).

Don´t know if this is important or original souncdore.ko (the one that comes with Ubuntu 6.10) works for any alsa version

---

### Post by MrNobody on 2007-04-12
More info...
Doing cat /proc/asound/cards:

 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe028000 irq 10

And lsmod | grep snd:

snd_hda_intel          24604  5 
snd_hda_codec         252032  1 snd_hda_intel
snd_pcm_oss            57856  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm               108040  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              30600  2 snd_pcm
snd                    81192  14 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              14112  1 snd
snd_page_alloc         14224  2 snd_hda_intel,snd_pcm

I was wondering if maybe, another module should be loaded instead of snd_hda_intel for Realtek ALC861, when using drivers downloaded from Realtek.

---

