---
title: "rhythmbox mp3 playback"
date: 2010-02-01
forum: Multimedia Software
---

### Post by amc32 on 2010-02-01
Hi,
I tried to play a music file w/ rhythmbox, but it needed a plug-in. When I searched for it, there was none to be found. I need to know how to install plug-ins in order to play my mp3's and movies.

---

### Post by maritza on 2010-02-01
HI,
go to "System" - Package manager- type what you need in the searchengine and rightclick Mark for Installation- apply- bingo
good luck:D

---

### Post by amc32 on 2010-02-01
I tried the suggestion, but rhythmbox still says a plug-in is missing and will not play audio.

---

### Post by skierkyles on 2010-02-01
Hi, the easiest way to install mp3 playback is by installing the ubuntu-restricted-extras package, which you can install by clicking this: 

[apt:ubuntu-restricted-extras](apt:ubuntu-restricted-extras)

Note: Installing that package will also install codecs for almost every other video/audio format there is. And browser plugins like flash and java. But you probably will need all that anyway.

Or you could install just the mp3 codec by clicking this:

[apt:gstreamer0.10-fluendo-mp3](apt:gstreamer0.10-fluendo-mp3)

Then restart rhythmbox, and you should be set!

---

### Post by amc32 on 2010-02-01
Thanks a lot, things are working correctly now. Appreciate you taking the time to help.

---

