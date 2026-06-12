---
title: "Dolby 5.1 Surround with Intel HDA?"
date: 2009-08-28
forum: Multimedia Software
---

### Post by foxmajik on 2009-08-28
Hello,

In Windows there is an application for my onboard Intel audio that allows me to get *Dolby 5.1 Surround* audio so that all the proper audio channels are sent to the proper speakers (front L/R, rear L/R, center and LFE) such that I get genuine *Dolby 5.1* audio from music.

This doesn't seem to happen in Ubuntu 9.04.  I can't find any controls for it anywhere and there doesn't seem to be any application that would let me switch it on or off.

I have found plenty of tutorials that will tell me how to do things like [make the stereo image from the front channels also play through the other speakers]("http://ubuntuforums.org/showthread.php?t=795525"), but that doesn't quite fit the bill, as it were.

I've done lots of searching and I can't find any information on how to get any sort of *Dolby Surround* audio on any device with any sound server (I also have a *Creative Audigy* which is capable of *Dolby 5.0* but again, I can't find any way to switch it on).

Can anyone offer suggestions on how to get my Intel HDA audio to work in **Dolby 5.1** rather than just playing the same two channels on the surround speakers?

Failing that, is there any device I can get that will output Dolby 5.1 audio in Ubuntu?

Thanks in advance.

---

### Post by foxmajik on 2009-09-15
Answering my own question:

All I had to do was install Pulseaudio from the project's launchpad sources, delete .pulse* from my home directory and restart my computer.

After that I had new options available on the Configuration tab of the Volume Manager:

[IMG]http://imgur.com/qrYJi.png[/IMG]

---

