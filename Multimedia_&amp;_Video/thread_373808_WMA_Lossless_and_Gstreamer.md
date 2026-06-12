---
title: "WMA Lossless and Gstreamer"
date: 2007-03-01
forum: Multimedia &amp; Video
---

### Post by MonkeyFit on 2007-03-01
I can't get Gstreamer to play my WMA Lossless files at all.  Other players on my system handle these files just fine.  But in the command line, I get this:
```

user@linux:~$ gst-launch-0.10 playbin uri="file:///media/usbdisk-1/Music/Rammstein/Mutter/03%20Sonne.wma"
Setting pipeline to PAUSED ...
Pipeline is PREROLLING ...

(gst-launch-0.10:5808): GStreamer-WARNING **: pad asfdemux0:audio_00 returned caps that are not a real subset of its template caps
** Message: don't know how to handle EMPTY
ERROR: from element /playbin0: You do not have a decoder installed to handle this file. You might need to install the necessary plugins.
Additional debug info:
gstplaybasebin.c(1663): prepare_output (): /playbin0
ERROR: pipeline doesn't want to preroll.
Setting pipeline to NULL ...
FREEING pipeline ...
user@linux:~$

```

They played just fine on Dapper, but not now on Edgy.  Does anybody know why this is?  I have installed every Gstreamer-0.10 plugin I could possibly find reference to: good, bad, ugly, ffmpeg, pitfdll, w32codecs, the list goes on.  I know I could just use one of the other players, but the whole point of getting Gstreamer to play it is so that Songbird will play it.  Can anybody help me?

---

### Post by MonkeyFit on 2007-03-28
shameless bump

---

### Post by jfca283 on 2007-03-29
you must install this library
**gstreamer0.10-pitfdll**
with this you will be able to listen wma files or watch wmv videos

---

### Post by jasontan6 on 2007-11-10
> **jfca283 said:**
> you must install this library
**gstreamer0.10-pitfdll**
with this you will be able to listen wma files or watch wmv videos

Not working. Using Gutsy and Rhythmbox. Rhythmbox on its own does not add WMA lossless files into the library when set to scan for such files in folder. When manually imported a WMA lossless, Rhythmbox throws an Import error: "The Gstreamer plugins to decode "Unknown" cannot be found."

---

### Post by StickyCube on 2008-01-20
I had this problem, and got it fixed.  I'm not sure which was the critical package, so I'll list all that I used.
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-ugly
(possibly also the '-multiverse' versions of those two)
libaudio-wma-perl
hope this helps.

---

