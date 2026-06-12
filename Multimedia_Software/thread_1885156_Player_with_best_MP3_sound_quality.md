---
title: "Player with best MP3 sound quality"
date: 2011-11-22
forum: Multimedia Software
---

### Post by aura7 on 2011-11-22
I am currently using Rhythmbox on Ubuntu 10.04, but I am not satisfied by its sound quality in playing mp3 songs. I am also using iTunes on Windows which gives awesome sound quality. I have already tried Banshee.. and the problems remains the same.

Can anyone suggest a media player with good sound quality for mp3 songs. Interface can be bad but I need great quality of sound.

---

### Post by QuantikTar on 2011-11-22
All players on the gstreamer framework uses MAD library to play mp3 files, [http://gstreamer.freedesktop.org/apps/](http://gstreamer.freedesktop.org/apps/)

And MAD is the best MP3 decoding library so far. (I was using it with winamp when I was still on windows, and there was a real quality improvement in comparison with the standard decoder plugin)

Banshee uses gstreamer, so I suspect your sound quality problem is not coming from the player but from the system.

What is your sound card? And what is exactly the quality problem? (crackling sound, loss of sharpness, etc...?)

---

### Post by alphacrucis2 on 2011-11-22
As the previous poster mentioned it may be nothing to do with the player. If you are using the pulseaudio sound server which ubuntu does by default it may be that you need to configure a better resampling method.

See this page:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Particularly pertaining to this question heading:

**Q. I'm unhappy about the audio quality / CPU usage of PulseAudio. How do I change this?**

Note that you can change the resampling method from the worst, namely "trivial", through to the best "src-sinc-best-quality". I forget what default is set in Ubuntu. I have speex-float-3 set which seems a reasonable compromise between performance and quality. 

It is also worthwhile to install the pulseaudio equalizer which allows you to have global equalizer settings.

---

### Post by aura7 on 2011-11-22
Speakers are fine I as it is giving good quality sound with iTunes on Windows.

Thanks alphacrucis2

---

### Post by cottfcfan on 2011-11-23
aura7...
I've always found Exaile to give the best quality sound.
Just tweak the Equaliser slightly & disable Replay Gain in plugins.

---

