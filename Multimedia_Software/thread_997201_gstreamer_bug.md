---
title: "gstreamer bug"
date: 2008-11-29
forum: Multimedia Software
---

### Post by billd42 on 2008-11-29
I was recently trying to burn an audio CD from .wav files on Intrepid Ibex.  I got an error message that "Track is less than six seconds--six seconds will be added to track" and got a display full of six-second tracks.  GnomeBaker estimated the length of all the tracks at zero.

In addition, gstreamer-based software would not play .wav files correctly.

I did some digging and found the following:

This is likely due to [bug 561580 in gst-plugins-good that was submitted to gnome]("http://bugzilla.gnome.org/show_bug.cgi?id=561580") earlier this month.

This should fix [bug 298939]("https://bugs.launchpad.net/ubuntu/+source/gst-plugins-good0.10/+bug/298939").

Hopefully the repositories get updated soon.

---

