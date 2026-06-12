---
title: "which audio server for Festival?"
date: 2009-03-22
forum: Multimedia Software
---

### Post by DaveDrPop on 2009-03-22
Hi all

Trying to get festival to work - at the moment I'm getting this error

festival> (SayText "Hello")
ALSA lib confmisc.c:768: (parse_card) cannot find card '0'
ALSA lib conf.c:3513: (_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392: (snd_func_concat) error evaluating strings
ALSA lib conf.c:3513: (_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251: (snd_func_refer) error evaluating name
ALSA lib conf.c:3513: (_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985: (snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2145: (snd_pcm_open_noupdate) Unknown PCM default
aplay: main:546: audio open error: No such file or directory

What I'm confused about is that I still get this error despite having selected pulseaudio for everything in System->Preferences->Sound

The Ubuntu documentation says you can use ESD or Alsa as well- which one is the best one to use?

I have also tried padsp festival, and tried the same thing, and got a segmentation fault :(

The sound card I have is one of those cheapy USB ones (which plays audio files just fine), and I am running Hardy server

any help appreciated

Dave

---

