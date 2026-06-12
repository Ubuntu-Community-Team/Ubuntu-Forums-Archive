---
title: "Alsa device not working with ogg123"
date: 2012-04-09
forum: Multimedia Software
---

### Post by K-Jtan on 2012-04-09
Hi everyone,

I have a server running at home on which I stream my music 24/7 using icecast. Today I tried to listen my music on that specific computer using command line (I don't have a screen for that computer so need to access it by ssh).

so since icecast is streaming the music in ogg format, I tried using ogg123 and I got an Alsa error. 

This is what was display in the terminal
```
~$ ogg123 http://localhost:8000/mymusic.ogg

Audio Device:   Advanced Linux Sound Architecture (ALSA) output

                                                                                                 
Playing: http://localhost:8000/mymusic.ogg
Ogg Vorbis stream: 2 channel, 44100 Hz
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.front
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:4184:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:4184:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:4184:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4663:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM default
ERROR: Cannot open device alsa.
```Do I need to configure a file ? If yes, how do I do that ?

Thank you very much
Cajetan

---

