---
title: "Select sound output device for Flash"
date: 2009-12-23
forum: Multimedia Software
---

### Post by spiritofcat on 2009-12-23
The onboard sound in my computer stopped working, so I got myself a little USB sound card.
After a bit of trial and error I have sound working in Ubuntu (Notification sounds etc), Movie Player and VLC.
In VLC I had to change Audio Output Type to UNIX OSS audio output with device /dev/dsp1

I haven't found a way of telling flash player in firefox to send the sound to the USB card and not the broken onboard card though.

Anyone got any tips? I'd like to be able to watch things on YouTube again.

Edit: decided to try out a couple more auido playing apps.
Couldn't get any sound out of GNOME MPlayer.
Got MPlayer Movie Player to work by setting it to oss driver using device /dev/dsp1
Rhythmbox Music Player worked all by itself.

Seems that oss and /dev/dsp1 are the key factors here, but I've had to specify them manually in half the programs I tried.
Surely there is some way to set the defaults for the operating system to oss and /dev/dsp1 so that all audio programs work automatically.


Edit: Well I found a solution. I simply disabled the onboard sound card in the bios so now the USB one is the only one active and everything uses it automatically.

---

