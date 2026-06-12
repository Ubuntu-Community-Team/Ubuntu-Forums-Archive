---
title: "[SOLVED] Issue with Rear Speakers using Audigy2"
date: 2008-11-30
forum: Multimedia Software
---

### Post by greyfox1 on 2008-11-30
Sorry if this has been answered in another thread, but I couldn't find this same issue resolved anywhere else.

I've been having trouble getting sound out of my rear speakers (I have a 4.1 setup).  I followed the instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=770028") and was at least able to get sound out of the rear speakers when I issue:

```
speaker-test -Dplug:surround51 -c4 -l1 -twav
```

...but nothing when playing music or videos (Totem, Banshee, or Flash) I only get sound out of the front speakers.  Is this a gstreamer problem?  Any help would be appreciated.

---

### Post by greyfox1 on 2008-12-01
bump

---

### Post by greyfox1 on 2008-12-04
Bump plz

---

### Post by element_G on 2008-12-04
Sound from those apps is in Stereo (L and R channels only) so your sound card is playing just that. You have to tell your sound setup to duplicate the front sound to the rear in order to make stereo sound go through all four speakers. 

The best way to do this that I know of is through pulseaudio.
You will have to follow "the hard way" for your 4.1 speakers but this should help:
[http://ubuntuforums.org/showthread.php?t=795525](http://ubuntuforums.org/showthread.php?t=795525)

---

### Post by greyfox1 on 2008-12-10
Hmm, interesting.  Despite the info given in the guide you linked to, I got it working using the "Easy" method (and my subwoofer still works!).  I think I probably have the front speakers mirrored to the rear rather than true surround, but that's all I wanted to begin with.

Thank god, I was about to go nuts on this one.  Thanks a lot!!

---

