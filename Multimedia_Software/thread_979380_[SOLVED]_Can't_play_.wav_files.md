---
title: "[SOLVED] Can't play .wav files"
date: 2008-11-11
forum: Multimedia Software
---

### Post by timroberts on 2008-11-11
For some reason i'm unable to play .wav files in any of my available media players (songbird, rhythmbox). I have ubuntu-restricted-extras installed, as well as ffmpeg and w32codecs. My sound settings are all set to use ALSA, and can play any mp3 or m4a without any problems. Any help would be appreciated. Oh, i'm using 8.10 too.

---

### Post by SunnyRabbiera on 2008-11-11
Strange, as .wav should play after all the codecs are installed and such

---

### Post by timroberts on 2008-11-11
hence my confusion as to why it won't play.

---

### Post by mc4man on 2008-11-11
i always thought .wav's would play 'out of the box' so to speak.

If you can't find a solution your best bet for generating an error message is to use mplayer from the cli. 
mplayer /path/to/name.wav
for instance drop a .wav in home folder and go 
mplayer ~/[COLOR="Red"]foo[/COLOR].wav

---

### Post by timroberts on 2008-11-12
not sure why, but that did it. Thanks!

---

