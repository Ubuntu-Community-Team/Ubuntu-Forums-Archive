---
title: "Exaile and VLC issues."
date: 2008-06-10
forum: Multimedia Software
---

### Post by linux phreak on 2008-06-10
I am running xubuntu 8.04.Whenever i play a song using Vlc,the player hangs for a while and starts playing the song after a few seconds there by skipping some of the beginning of the song.The same goes for video.The vlc version is 0.8.6e.I do not remember having this issue in 7.10.Also exaile's inbuilt equalizer is having no effect whatsoever to the sound playback.All the presets are not working or having any effect.

---

### Post by argail1980 on 2008-06-10
try playing around with different video/audio output modules, that did the trick, when I had a similar problem. I had a few seconds pause at the start of every video and the sound was hanging everytime I did something else than watching the video. The cause was that damnable pulseaudio plugin. Try alsa for adio or some other video plugin.. I don't know exactly where these settings are, because I have a german interface. settings -> advanced options... something like that

---

