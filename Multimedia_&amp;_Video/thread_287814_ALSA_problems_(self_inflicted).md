---
title: "ALSA problems (self inflicted)"
date: 2006-10-29
forum: Multimedia &amp; Video
---

### Post by bignickel on 2006-10-29
I udgraded to Edgy with no real problems, but then I started messing around with my sound, and have had nothing but problems since.  My problem was trying to install pulseaudio.  I never got it to work so I removed it, and now ALSA is giving me all kinds of errors.  I tried removing and reinstalling all the ALSA packages but it didn't help.  Basically, if I try to start a program like alsamixer, esd, or skype, I get an error like this:

ALSA lib control.c:781:(snd_ctl_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_ctl_pulse.so

alsamixer: function snd_ctl_open failed for default: No such file or directory

Sometimes there are more modules it can't open, but that's the general idea.  But amarok works fine.  What package do I need to install?  My /usr/lib/alsa-lib only contains libasound_module_pcm_jack.so.  I'm sure the solution must be simple, but I can't figure it out.  Please help!

---

### Post by npnutn on 2007-03-01
> **bignickel said:**
> ...I get an error like this:

ALSA lib control.c:781:(snd_ctl_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_ctl_pulse.so

alsamixer: function snd_ctl_open failed for default: No such file or directory


I was struggling with sound on thin clients with similar error messages until I installed the following with apt-get:

pulseaudio-esound-compat 
pulseaudio-module-hal 
pulseaudio-utils 
libasound2-plugins 
libasyncns0

I'm not certain this will fix your issue, but it's worth a try.

---

