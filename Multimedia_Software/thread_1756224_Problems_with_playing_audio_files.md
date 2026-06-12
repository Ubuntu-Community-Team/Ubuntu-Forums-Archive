---
title: "Problems with playing audio files"
date: 2011-05-12
forum: Multimedia Software
---

### Post by avi9526 on 2011-05-12
OS: Ubuntu 11.04
Audio: PulseAudio

I have next problems with music players:
1). Banshe and Rhythmbox - some mp3 files start playing with click or other bad short noises. When I click on time-slider and try to move it - I get many scary sounds.
2). VLC - by default use pulseaudio output. When mp3 file start play - after ~0.3 sec sound disappear for ~0.2 sec, and then appear again (but VLC do not have problems of prevision players). When I play mp4 audio - for first 0.4sec music have low volume, then step to normal playing. If set VLC output to ALSA - its begin playing well, but seems VLC lock alsa, and other applications can't do any sound.

But...
AIMP player (launched with Wine) working very good, and without making ugly sounds.

What is reason, and what to do to get normal sound with those players ?

---

### Post by lidex on 2011-05-14
Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*

---

### Post by avi9526 on 2011-06-30
Its doesn't help.

I try to remove some packages, now all players, except vlc, working fine.

Problem now only with vlc:
if no other program that play sound - vlc give some distortion on start of playback. I play some test file (simple sine wave) and get output (recorded from headphones)
[[IMG]http://storage8.static.itmages.ru/i/11/0514/s_1305376394_d2e7fcb7cb.jpeg[/IMG]]("http://itmages.ru/image/view/189582/d2e7fcb7")
It's easy to see the annoying distortion at t=0.35 sec. But, if some program already play sound - vlc play good, and no distortion. Anyone have ideas?

---

