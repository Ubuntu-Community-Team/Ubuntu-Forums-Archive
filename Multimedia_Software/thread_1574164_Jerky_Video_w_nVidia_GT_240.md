---
title: "Jerky Video w/ nVidia GT 240"
date: 2010-09-13
forum: Multimedia Software
---

### Post by antar on 2010-09-13
So first, the issue:

Video playback is sporadically jerky. This is the case for video in games, playing back AVI files (Totem), editing videos in Avidemux... haven't actually observed it for flash videos, ironically...

Now for my setup:
Ubuntu 10.04 x64
AMD Phenom 1090t (3.2GHz x6) processor
4GB DDR3 RAM
nVidia GT240 w/512MB GDDR5 RAM
nVidia proprietary drivers installed (downloaded from website)
Dual display (twinview): 1920x1080 + 1024x768

I realize that this is probably not NEARLY enough information to do a proper diagnosis, but I'm hoping it's enough for a start?

---

### Post by antar on 2010-09-13
Okay, well I have yet to encounter the problem in VLC, so I suspect it's a codec issue. That fixes the video playback problem (though I would prefer to use Totem), but what about game cinematic playback and Avidemux? Any suggestions?

---

### Post by cchhrriiss121212 on 2010-09-14
Try turning off Compiz. For video playback you should use Smplayer with vdpau output, which will give you GPU acceleration.

---

### Post by antar on 2010-09-14
Turning off Compiz did nothing, alas. And, again, I think VLC will handle the video playback. It's the other video stuff that I'm concerned about now.

---

### Post by formaldehyde_spoon on 2010-09-14
Sorry I can't offer anything more helpful, but I think you're correct in assuming it isn't your hardware: my machine is almost identical to yours (just based on what you posted) and I don't have any problems with video playback etc..

---

### Post by antar on 2010-09-14
Are you using the GStreamer codecs? (I am) Also, where did you get your nVidia drivers? I'm thinking maybe I'd have better luck if I installed the proprietary drivers through the PPA?

---

### Post by antar on 2010-09-14
Okay, you all want to hear something REALLY weird? All these problems go away... if I have VMWare Player running. Not as in, if I run my applications THROUGH VMWare Player... just if I have my virtual machine open, but I'm ignoring it.

Really weird.

---

