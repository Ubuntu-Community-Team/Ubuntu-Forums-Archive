---
title: "alsa problem: libasound_module_pcm_pulse.so"
date: 2009-10-14
forum: Multimedia Software
---

### Post by nicgios on 2009-10-14
Dear all,

Please erase this post if already solved (I looked around but found nothing). 

After an installation of Sunbird (yes the calendar program) my audio (wav files and flash movies in firefox) does not work any more.

Here is the problem (bash output when trying to see a movie on youtube):

ALSA lib pcm.c:2052:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
ALSA lib pcm_plug.c:1128:(_snd_pcm_plug_open) Unknown field hint


Bash output when trying to listen a wav (with play):

ALSA lib pcm.c:2052:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-
lib/libasound_module_pcm_pulse.so
play formats: can't open output file `default': cannot open audio device


Midi files work... :)

Any idea? Thanks in advance.


ps. Ubuntu-Studio Jaunty...

---

