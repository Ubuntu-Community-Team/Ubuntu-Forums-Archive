---
title: "REMOVAL of PulseAudio conflict with ALSA"
date: 2008-07-17
forum: Multimedia Software
---

### Post by persian_x on 2008-07-17
Hey people Its been days I've been trying to make my sound work on amd64 GUTSY, finally I managed to do that except for FLASH 9, thats when my nightmare began with PULSEAUDIO
Once I installed it, I didnt any sound at all so I completely removed it and now I am having trouble with ALSA and AlsaMixer, I do get that "drum" sound before logging in and some (and i mean SOME) videos have sound on VLC player but nothing else... Definitely conflict between PULSEAUDIO (what remains of it) and ALSA.

I get this error when typing ALSAMIXER:

ALSA lib control.c:874:(snd_ctl_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_ctl_pulse.so

alsamixer: function snd_ctl_open failed for default: No such file or directory


can anyone please help?

---

### Post by markbuntu on 2008-07-17
I wrote this little guide for myself a few weeks ago because I got fed up with my sound system problems and all the myriad of conflicting advice that just kept making it worse. After weeks of going in circles I finally got something that works for me all the time on both 32 and 64 bit installs.

It basically puts ALSA back in control but also lets pulse work to avoid the common conflicts. it is here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

