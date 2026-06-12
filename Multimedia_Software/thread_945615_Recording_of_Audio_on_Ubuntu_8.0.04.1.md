---
title: "Recording of Audio on Ubuntu 8.0.04.1"
date: 2008-10-12
forum: Multimedia Software
---

### Post by rksingh54 on 2008-10-12
I am trying to record music that I can play from a website. I am unable to record the music while they are playing; no matter what. I have tried Sound Recorder but have no idea how to use this. These musics are from 40's and 50's, and have no more patent restrictions on them. Can anyone help me record thses that I can play on my Ubuntu 8.04.01? Again these music are on a website where one can log in and listen.

---

### Post by patrickballeux on 2008-10-12
Have a look at the "jack" package in wich you can connect any source to any sink.

Here an easy way to use Jack and PulseAudio together giving you the flexibility to record anything played over the pulseaudio server:

[http://webcamstudio.wiki.sourceforge.net/Flash+and+Jack]("http://webcamstudio.wiki.sourceforge.net/Flash+and+Jack")

It was meant to make Flash record from Jack, but it could also be used to record from Flashplayer or any source connected to PulseAudio.

Essentially, you will need Jack Control (jackctl) to start and configure your jack server, and connect your source with your sink (microphone...) so you will be able to record from jack or from pulseaudio.

Be prepared to do some readings on jack to know how to use it, but it is not really hard as you will see...

Good luck!

---

