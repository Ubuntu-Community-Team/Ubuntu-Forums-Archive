---
title: "Sound only playing for one application at a time"
date: 2009-08-27
forum: Multimedia Software
---

### Post by Rogue Jedi X on 2009-08-27
This is a problem that started occurring just recently, more than likely due to a fault of my own. Example of the problem: If Amarok plays, Kopete won't make that *ding* sound when a message arrives, youtube videos are silent and mplayer reports a playback error due to the sound device being busy.

I know this wasn't the case when I installed Kubuntu 9.04. In fact, multiple apps playing at once was one of the features I first noticed as this wasn't the case on KDE 3.

The two causes I could think of:
a) Doing "sudo apt-get dist-upgrade" two or three times. My update manager was holding back updates.
b) When I was messing around with [icculus' Quake 2 port]("http://icculus.org/quake2/") I did the following in hopes of getting sound to work (Not worth the effort for those interested, too many patches need applying and doesn't play well with 64-bits. Get [Yamagi Quake II]("http://www.yamagi.org/quake2/") instead.):
```
SDL_DSP_NOSELECT='0'; export SDL_DSP_NOSELECT
```

I have Kubuntu 9.04 64-bit. Any help would be greatly appreciated.

---

### Post by sm2uyn on 2009-09-14
*bump*

I have almost the same problem. I can only have sound from one program at a time. However, for me any new sound interrupts the previous. E.g. if a kopete message arrives when listening to Amarok, Amarok goes silent and I have to stop-play cycle to get the music back.

Also using Kubuntu 9.04 64-bit. Any help would be greatly appreciated.

---

