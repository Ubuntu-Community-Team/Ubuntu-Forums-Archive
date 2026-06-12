---
title: "Sound: Some programs work, others silent and others sound weird"
date: 2008-04-09
forum: Multimedia &amp; Video
---

### Post by thomashauk on 2008-04-09
I am attempting to get sound working on an external USB device however I a having dificulties.
In some programs the sound works fine, e.g. xmms
In other it is just silent, e.g. totem
In others it throws up errors and doesn't work, e.g. mplayer
and weirdly in rhythembox it just sounds weird, but remotely like what I am attempting to play.

Anyone know what is going on?

---

### Post by jeffus_il on 2008-04-09
Which driver is Xmms using?
You can find it in the preferences.
Totem comes in two versions, one gstreamer, one Xine, you can see which one you have installed using the About menu. 
Rhythmbox uses gstreamer.

You may have a problem of missing Gstreamer and/or other libraries.

---

### Post by thomashauk on 2008-04-10
XMMS is outputing to alsa to USB audio as it should,
Totem is using xine

It has turned out the rhythmbox had acutally managed to distort the mp3's themselves not just played them distorted.

Flash does not have sound.
Realplay (need it for listening to BBC stuff) errors with "Cannot open the audio device. Another application may be using it."
gmplayer errors with: "Could not open/initialise audio device -> no sound"

---

### Post by thomashauk on 2008-04-11
Tried skype and the sound was the same as in rhythmbox all distorted

---

