---
title: "Have to kill PulseAudio for sound"
date: 2008-08-13
forum: Multimedia Software
---

### Post by nontrivial on 2008-08-13
I listen to streaming audio (XM Radio) while at work using Firefox and the mplayer plugin. The default plugin does not work for XM Radio. When I go to lunch and take long enough such that the monitor is suspended I have to kill the pulse audio processes (pulseaudio and gconf-helper) before I can listen to the streaming audio again. I am using i386 32 bit Hardy Heron.

James
PS Not to mention the random failures logging out that I continue to enjoy.

---

### Post by leepesjee on 2008-08-13
This seems to be another variant of the ubiquitious problems with pulseaudio. The thing is that pulseaudio needs exclusive use of alsa. So either you have pulseaudio over alsa, or you have (any) other application playing over alsa. You can't have both.
I cannot say exactly say what your problem is, it depends on your setup. If you need to kill pulseaudio to get sound from mplayer, that probably means that mplayer is set to play over alsa directy. You can try to set this to pulseaudio (this can be done in gmplayer's preferences, I guess that also counts for the plugin then).

---

### Post by markbuntu on 2008-08-13
This is a known bug in Pulseaudio and is related to gconf, failure to resume after system suspend causes the pulseaudio daemon to hang on some systems resulting in no sound service. Gconf also causes logout problems on some systems.

Monitor only suspend should not cause these problems, only system suspend.

---

### Post by eye208 on 2008-08-14
PulseAudio is optional. You can completely remove it and run all your sound straight through ALSA.

---

### Post by TenPlus1 on 2008-08-14
That's what I did and my sound works perfectly...  Alsa works great!

---

### Post by bennyturok on 2010-08-01
worked!!!   rosetta stone now detects my audio driver and its usable.  thanks allot :)

---

