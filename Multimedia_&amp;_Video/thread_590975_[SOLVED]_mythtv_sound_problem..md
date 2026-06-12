---
title: "[SOLVED] mythtv sound problem."
date: 2007-10-25
forum: Multimedia &amp; Video
---

### Post by applegrew on 2007-10-25
My audio chipset loks very complicated. I have manged to get it to work with tvtime, mencoder and mplayer, but still not MythTV. :( For mencoder I use the alsa and adevice=default as options for v4l2 driver to capture the sound.

Using a cable I have piped the line-out of my Intex TV capture card to my Line-In of the sound card. Below is my present setting for the sound card as show by gnome-alsamixer.

---

### Post by applegrew on 2007-10-25
I just got a very encouraging result. :D
I just now by-chance started TVTime while watching a video on MythTV and then there it is, MythTV was able to capture the sound and record it and broadcast it.

Now what did TvTime do that allowed MythTV to capture the sound? MythTV is capturing the sound from /dev/dsp while TvTime is running with its default values which I don't know.

Now can somebody help me so that I don't need to turn on TvTime everytime I start MythTV. Pls help.

---

### Post by applegrew on 2007-10-25
I now tried this with

mplayer tv:// -tv driver=v4l2:norm=PAL:alsa:adevice=default -vo null 

and it works but since it blocks the video if I run it first hence I need to manually run it once I start the LiveTV of MythTV.

Is there a way to only open this audio device and not the video device?

---

### Post by applegrew on 2007-10-26
I just came by to say that I have fixed this. For all people who faces similar situation, here's what I did. I simply put **v4lctl volume mute off** as the startup command in mythtv-setup.

---

