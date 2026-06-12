---
title: "Alsa errors"
date: 2006-12-03
forum: Multimedia &amp; Video
---

### Post by falkenberg_cph on 2006-12-03
Hi
I have gotten this strange error after installing the newest alsa. I have also tried to reinstall, it didnt help. Maybe you who are sound experts can help me. The below example is from my terminal, where im running a c++ script. I get the same errors after fx. editing a documents through the terminal (sudo gedit /....):

Here goes /Carsten

> carsten@carsten-laptop:~/Desktop/C++$ ./test-sdl
ALSA lib confmisc.c:1105snd_func_refer) Unable to find definition 'defaults.pcm.dmix_format'
ALSA lib conf.c:3500_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3957snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2143snd_pcm_open_noupdate) Unknown PCM dmix:SI7012
carsten@carsten-laptop:~/Desktop/C++$

---

