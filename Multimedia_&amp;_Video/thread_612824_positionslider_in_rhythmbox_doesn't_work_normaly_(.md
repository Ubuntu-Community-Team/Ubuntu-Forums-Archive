---
title: "positionslider in rhythmbox doesn't work normaly (stops or skips randomly when used)"
date: 2007-11-14
forum: Multimedia &amp; Video
---

### Post by hansie99 on 2007-11-14
Hello,

I have an annoying problem with rhythmbox to play mp3s using Ubuntu 7.10. I had the problem also in 7.04. I can play mp3s just fine, but I can't seem to use the positionslider to rewind, fastforward in a normal way. When I use it the mp3 stops and refuses to play any longer or skips to a random location. In last case I often hear a very high pitched sound which is very annoying with headphones... 

Anyone a solution to this problem? I know I listen to music in a strange way... :) most people probably would listen to a song and never skip back or forward, but I often do... 

I tried to change the sound settings in system/sound. Tried OSS and Alsa and al other possibilities, but no luck. It doesn't matter which one I use, the results are the same. I have so far found out that it is most likely a gstreamer issue. Anyone an idea? Should I change to something else than gstreamer? How do I do this? Or use another player perhaps? 

Another sound issue I have is that the systemsounds are always loud! I can't change their volume. I tried al posibilities in the mixer (alsa and oss) but I can't change it to a more suitable level. Any ideas? I am a noob when it comes to sound in Linux so please help me out. Thanks in advance!

---

### Post by hansie99 on 2007-11-25
```
set s_alsa_pcm plughw:0

```

solved my issue! So this was an ALSA misconfiguration? Anyway, everything works fine now.

Cheers!

---

