---
title: "No Sound ubuntu 6.10"
date: 2007-02-14
forum: Multimedia &amp; Video
---

### Post by gu014 on 2007-02-14
Hello,
I am not sure if this is in the correct forum, but here it is:

I am using Openbox.
I am using a DFI Lanparty nF4 SLI-DR motherboard with the onboard 8-channel sound card.

My sound is not working in Mythtv under ubuntu 6.10. Here are a few commands i used to verify that the sound board is recognized:
```
lsmod | grep snd
snd_intel8x0           42024  0
snd_ac97_codec        127064  1 snd_intel8x0
snd_ac97_bus            4352  1 snd_ac97_codec
snd_pcm_oss            57344  0
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm               108168  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              31112  1 snd_pcm
snd                    79016  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              14112  1 snd
snd_page_alloc         13200  2 snd_intel8x0,snd_pcm

```

```
 cat /proc/asound/cards
 0 [CK804          ]: NFORCE - NVidia CK804
 NVidia CK804 with ALC850 at 0xfe02d000, irq 225
```

I have verified that 'alsamixer' does not have the channel muted.  

Any help would be greatly appreciated.  Thank you.

---

### Post by LinuxDevil on 2007-02-27
same here .... i`ve tried 1000 tweaks, configs, filters etc (exagerating a little bit ;) ), but still only 2 out of 8 audio channels are working... i don't know what to do anymore... pls HELP US some one!!!

soundcard details:
=====================================================
NFORCE - NVidia CK804
NVidia CK804 with ALC850 at 0xec105000, irq 225
=====================================================
lsmod | grep snd
snd_intel8x0           34844  1 
snd_ac97_codec         97696  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
snd                    58372  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
=====================================================

---

