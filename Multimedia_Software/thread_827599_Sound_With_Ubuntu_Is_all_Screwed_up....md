---
title: "Sound With Ubuntu Is all Screwed up..."
date: 2008-06-12
forum: Multimedia Software
---

### Post by morbidxbean on 2008-06-12
Sound works for youtube videos but when i try to listen to some mp3's or listen to a cd...or watch a video...i get no sound..

---

### Post by AndThenWhat on 2008-06-12
See if you can close your web browser and then try opening an mp3.  If your sound works on the mp3 after you close your browser, then you have the same problem I have.

---

### Post by morbidxbean on 2008-06-12
Nope I still cant hear the files...and when click to play them (in the media player) they will have a little red stopsign lookin thing come up next to em.

---

### Post by AndThenWhat on 2008-06-12
You could try going to System -> Preferences -> Sound and playing around with the settings.  I know that ALSA has better support for playing multiple sounds at once.

---

### Post by TheApe on 2008-06-12
Hi man.
I had the same problem and found the solution here on the forums.

```
sudo apt-get install libflashsupport
```

See the package description:
>>
Description: Support library for sound output of Flash 9 with pulseaudio Due to various bugs in the Flash 9 plugin sound output of Flash 9 through the pulseaudio soundserver doesn't work properly. This library adds a clutch to make Flash 9 sound output in pulseaudio possible.
<<

I just don't know why it's not installed by default...

:)

---

### Post by mastermindg on 2008-06-13
It's not installed by default because Flash is a nonfree addon to Ubuntu. You have to install these manually.

---

