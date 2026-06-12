---
title: "Play mp3 sound from script using gstreamer"
date: 2009-04-28
forum: Multimedia Software
---

### Post by koma77 on 2009-04-28
I have a bunch of sound files that I want to play from within a script.

So far I have been calling mplayer for the job but I've discovered that it cannot play really short mp3-files! And neither can VLC. And almost all of my sound files are really short (< 5K)

However, totem can, but it is GUI only, so I cannot use that.

Is there some other player that I can call from command line?
Totem is using gstreamer I believe. Are there more?

---

### Post by kostkon on 2009-04-28
You can try with *aplay*. It comes with Ubuntu by default thus you don't have to install it.

---

### Post by koma77 on 2009-04-29
I tried aplay, but it won't play these MP3s...
I don't think aplay is capable of playing MP3?

---

