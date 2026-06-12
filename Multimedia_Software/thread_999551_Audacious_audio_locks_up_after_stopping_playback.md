---
title: "Audacious: audio locks up after stopping playback"
date: 2008-12-02
forum: Multimedia Software
---

### Post by bburtin on 2008-12-02
I recently upgraded from Hardy to Intrepid and started having problems with Audacious.  Playing audio works fine, but sometimes when I hit "stop", Audacious locks up and I hear the last split-second of audio looping through the speakers over and over.  The noise persists even if I kill Audacious.  The only workaround I have found is to reboot.  I switched SMPlayer and haven't seen the problem yet, so it may be specific to Audacious.

Is anyone else seeing this?  Any ideas about a workaround?  I'm using a Dell Latitude D620.  lscpi shows this:
```
$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
```

---

