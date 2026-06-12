---
title: "No 2 sound sources at once"
date: 2009-06-02
forum: Multimedia Software
---

### Post by Patrick Snyder on 2009-06-02
If I'm using sound in one thing (eg: Skype) I can't hear sound in another (eg: youtube on Firefox).  There's also a weird thing where the video (picture) will stop playing with no way to start it again.  And quite often Firefox freezes/crashes after that.

This goes both ways: Flash Video -> Skype / Skype -> Flash Video, and seems to affect other applications like Amarok.  If I leave a Skype call, then restart Firefox, the videos will play sound again.  If I've played video in Firefox, I need to close it before using Skype.

Movie Player seems to be the only thing that consistently gives me sound even while some other sound is playing.


It's quite possible I borked the sound settings somehow.  I messed with them in 8.10 to get Skype working and recently upgraded to 9.04 which is where the problems started occuring.


How do I diagnose what's going on here?

---

### Post by HavocXphere on 2009-06-02
You need to set up pulseaudio correctly.

There is a huge tutorial somewhere here that Markbuntu wrote...

Found it
[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

---

### Post by Patrick Snyder on 2009-06-02
Thanks (^_^)

I followed the instructions and then in Skype's Sound Devices there was now a "pulse" option.  I used that and now it works while other things are playing.  Everything else seems smooth too.

Thanks again!

---

