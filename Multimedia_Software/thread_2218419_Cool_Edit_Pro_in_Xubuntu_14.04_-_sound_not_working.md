---
title: "Cool Edit Pro in Xubuntu 14.04 - sound not working"
date: 2014-04-20
forum: Multimedia Software
---

### Post by Bill Tetzeli on 2014-04-20
Hey all.  I just installed Cool Edit Pro in Wine, in Xubuntu 14.04 LTS, and whenever I try to play a sound file in it all I get is static.  In Wine configuration under the audio tab I changed all the setting from "default" to "pulse audio", still no go.  I'm a bit puzzled, since Cool Edit worked without a hitch in every previous version of Linux I've used.  Any ideas as to what it might be or how I can fix it?  If I'm not giving enough details, please tell me what you need and I'll try to provide them.

TIA

---

### Post by Bill Tetzeli on 2014-04-30
Success!  Instead of going through the regular Wine configuration dialog, I went into Winetricks and set the default sound driver to ALSA.  It would have been nice if it was set that way by default like it was on all my previous Linux and Wine installations (thinking of asking for a refund :P) but hey, it woiks! and that's the main thing.  Many thanks to fossfreedom for figuring it out three years ago and posting his reply on the askubuntu forum.  Here's the link:

[http://askubuntu.com/questions/77210/how-to-change-the-default-audio-in-wine-to-alsa-only](http://askubuntu.com/questions/77210/how-to-change-the-default-audio-in-wine-to-alsa-only)

---

