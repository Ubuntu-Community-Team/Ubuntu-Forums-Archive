---
title: "mac/virtualbox audio plays at lower sample rate"
date: 2010-08-26
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by cleentrax on 2010-08-26
I am running Maverick as a VM in Virtualbox on OS X 10.6.4 on the latest MacBookPro 15".

All software is updated to the latest version.

When I boot Maverick, the audio is muted. When I un-mute it, it plays at a lower/slower sample rate, as if it's expecting 48khz and downsampling it to 44.1khz, but was actually 44.1khz to begin with.

---

### Post by toobuntu on 2010-08-28
See [http://forums.virtualbox.org/viewtopic.php?f=8&t=29316&p=131576&hilit=ubuntu+no+sound#p131576]("http://forums.virtualbox.org/viewtopic.php?f=8&t=29316&p=131576&hilit=ubuntu+no+sound#p131576") and [http://forums.virtualbox.org/viewtopic.php?f=8&t=27835&p=124533&hilit=ubuntu+audio#p125765]("http://forums.virtualbox.org/viewtopic.php?f=8&t=27835&p=124533&hilit=ubuntu+audio#p125765")

On those forum posts, it is suggested to create the following file:
**/etc/modprobe.d/sound.conf** which should contain the following:
> options snd-intel8x0 ac97_clock=48000
options snd slots=snd-intel8x0
# AC'97 Audio Controller
alias snd-card-0 snd-intel8x0

I noticed the same thing you experienced when my kernel actually initialized my sound card. That happened only once. Every other time, I do not have access to an audio output device. No idea what's behind that. :confused:

---

### Post by cleentrax on 2010-08-28
Thanks, that did the trick. Not sure why I didn't find that on the vb forums.

---

