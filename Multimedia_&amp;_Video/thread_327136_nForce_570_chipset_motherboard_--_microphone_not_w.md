---
title: "nForce 570 chipset motherboard -- microphone not working"
date: 2006-12-28
forum: Multimedia &amp; Video
---

### Post by traherom on 2006-12-28
I have an Asus P5NSLI motherboard with an nForce 570 SLI chipset and
am having problems with the microphone. I got it working under Windows
(had to reboot into it for the first time in a few months :<), but
have had no luck under Edgy. I've played with all of the
alsamixer settings and such (See
[http://traherom.homeunix.net/alsamixer.png](http://traherom.homeunix.net/alsamixer.png), if you want to see the
current way they are), but still can't pick anything up.

A little bit of stuff which may help:
$ lspci
...
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
...

$ lsmod | grep snd
snd_hda_intel          20116  2
snd_hda_codec         164608  1 snd_hda_intel
snd_pcm_oss            47360  0
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25348  2 snd_pcm
snd                    58372  8
snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm

I have no clue what to do... I'm hoping someone here does. :)

Ryan

---

