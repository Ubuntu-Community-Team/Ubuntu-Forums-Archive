---
title: "Audio no louder than a whisper"
date: 2013-04-17
forum: Multimedia Software
---

### Post by ali_williams on 2013-04-17
hey guys,

If you have been following my posts I am running into all sorts of odd issues with Ubuntu on my most resent laptop. Anyway the latest thing to add to the pile is that the audio is no louder than a whisper. I have done the following.

sudo apt-get install alsa alsa-tools

sudo adduser myusername audio

then

$ alsamixer

Turned all of my levels up till all bars are full red. Then exit out of the app.

then did

sudo alsactl store

from there I launch my mp3 player and all I get is a faint noise. I am playing from the PC speakers so there is no other control over my volume. Do you guys know what else I could try?

---

