---
title: "Sound problems with ekiga/skype ALSA in 13.04"
date: 2013-05-01
forum: Multimedia Software
---

### Post by gunnvor on 2013-05-01
Xubuntu 13.04, ALSA, Intel(R) Core(TM)2 Duo CPU     P9500  @ 2.53GHz

I can play movies and audio streams with vlc, gmusicbrowser...

I can play and record my own voice with the embedded mic via

```
arecord -D plughw:0,0 -c 2 -r 16000 -f S16_LE - | aplay -D plughw:0,0 -c 2 -r 16000 -f S16_LE -
```

also with "c 1" instead of "c 2"

If Im using gmusicbrowser and try to execute any of those commands I get:

```
aplay: main:682: audio open error: Device or resource busy
```

Skype can play the automated voice message, but it sounds really awful, like an analogue conversation saturated with static electricity

Ekiga simply doesn't play any sound, and I have been following the linux instructions from their wiki (ALSA)

tips please.

What Im looking for: to be able to play music or a movie and, at the same time, talk with the embedded microphone with either skype or ekiga, receiving sound (incoming phone call) and being able to send soind (outgoing phone call)

much appreciated

---

