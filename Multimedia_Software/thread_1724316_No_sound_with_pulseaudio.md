---
title: "No sound with pulseaudio"
date: 2011-04-08
forum: Multimedia Software
---

### Post by burdebc on 2011-04-08
I tried to change to 5.1 from stereo and lost sound entirely.  To get sound back I had to uninstall pulseaudio, but that gives me sound only on my right front speaker and sub.  Whenever I install pulseaudio again I lose sound all over again.

---

### Post by Yellow Pasque on 2011-04-08
Did you just remove or did you purge ("completely remove") pulseaudio? If you didn't purge and reinstall, try that. There may be corrupted .pulse files/folder in your home directory. Creating another user and checking sound there may narrow down the issue as well.

---

### Post by burdebc on 2011-04-09
My front left speaker had a break in the cable, so I fixed that.  Now I have full stereo.  When I first purged pulseaudio I got 5.1 sound when I tested in phonon and sound would play in videos and such until movie player crashed with pa_stream_cork() and pa_stream_writable_size failures with avi, mkv, and ogm files.  I then changed the gstreamer sinks to alsa as recommended by this post ([http://ubuntuforums.org/showthread.php?t=1597682&highlight=vlc+sound](http://ubuntuforums.org/showthread.php?t=1597682&highlight=vlc+sound)).  This caused all videos that would give the pa_stream errors to skip ahead rapidly like they were fast forwarding.  I then tried to edit /etc/pulse/default.pa and include "tscreen=0" at the end of one of the lines (I can't remember which line as I can't find that thread again).  To get back to all videos playing porperly with stereo sound I purged pulseaudio and gstreamer0.10-pulseaudio.  Now with the gstreamer sinks changed to alsa even with pulseaudio and gstreamer0.10-pulseaudio installed all videos I have played except rmvb fast forward from a random point which so far has been different every time just as I mentioned earlier.

---

