---
title: "Help with restoring normal audio after using JACK and amsynth"
date: 2013-08-09
forum: Multimedia Software
---

### Post by Malcolm_Ragan on 2013-08-09
From looking at other threads I have it figured out that Jack disables pulseaudio and that pulseaudio must be restarted to restore normal system sound.  However I can't seem to figure out how to do that. The pulseaudio --start command that I have seen elsewhere is not effective.

EDIT: Ok... Nevermind. Ran pulseaudio -k and audio instantly came back

EDIT 2: No that's not right either. Apparently that brought back audio for Banshee (which uses ALSA?) and not normal system audio like I had thought

---

### Post by CatKiller on 2013-08-10
Having killed PulseAudio with -k you should try the --start again.

Personally I've always found JACK to hand back to PulseAudio quite smoothly without intervention, but I might have just been lucky.

---

### Post by marianoa on 2013-08-10
you could take a look at [this post]("http://ubuntuforums.org/showthread.php?t=2158480&page=3#28") of mine (sorry for self advertising :-) ), it's about having pulseaudio and jack work together seamlessly
[URL="http://ubuntuforums.org/showthread.php?t=2158480&page=3#28"]
[/URL]

---

