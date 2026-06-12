---
title: "No sound when playing AVI's"
date: 2009-08-04
forum: Multimedia Software
---

### Post by dmt0 on 2009-08-04
Hi all,
This one is beyond me.
I'm using Ubuntu Jaunty
I have sound in audacious, skype, flash video, but not when I play video in any of the video players: totem, vlc, mplayer.
The thing is that I do have all the codecs installed. Everything worked fine, and I can't quite trace the event that broke everything.
I have everything configured to use pulseaudio. I use on-board sound of nforce2 chipset.
I have 2 more sound devices -- an m-audio audiophile 192 -- which I never got to work on Ubuntu (a separate story), and a mic built into a usb camera. 
I used **pavucontrol** to make pulseaudio use several audio devices.
Still no luck with sound in video.
Any ideas?
Thanks guys!

---

### Post by dmt0 on 2009-08-06
bump!

---

### Post by dmt0 on 2009-08-08
Nobody has any ideas?

One more thing I can add is that I do get sound from video if I direct the output directly to OSS -- so it's definitely not the codecs but rather more like a pulseaudio issue. But it's painful since I have to turn off every program that might be using the device, and than my sound card gets assigned a different device file on every boot, so I have to go to the settings in the video player and manually change the device...

---

