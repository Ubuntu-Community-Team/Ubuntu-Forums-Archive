---
title: "Ripping CDs to MP3 stopped working after Ubuntu 6 upgrade"
date: 2006-10-21
forum: Multimedia &amp; Video
---

### Post by dwhsix on 2006-10-21
I was able to rip CDs to mp3 just fine when I was on Ubuntu 5.  After the (automatic) upgrade to Ubuntu 6, I can't.

The rip is done but the resulting file is about 10x the size it should be (e.g. maybe 30MB instead of 3MB), it's audio properties are all 'unknown', and it doesn't playback.  I was using the same gstreamer pipeline command I was using before.

Any thoughts?  What might I uninstall and reinstall to try and correct this?  So far searching in various places (including here) hasn't revealed anyone else having a similar problem.

Thanks,

dwh

---

### Post by dwhsix on 2006-10-21
Never fails... as soon as I ask a question, I find the answer.  [https://help.ubuntu.com/community/CDRipping](https://help.ubuntu.com/community/CDRipping) told me all I needed to know, which was I was missing the gstreamer0.10-plugins-ugly-multiverse package and the gstreamer pipeline had an additional item on it... all set now.

---

### Post by kwalo on 2006-10-22
Try ripping to ogg. You'll get better quality with better compression rate. Ogg format is free, so there are no problems with codecs on Ubuntu. If you plan to use these ripped files on your portable music player, make sure it supports ogg format

---

### Post by dwhsix on 2006-10-22
I know.  But I have an iPod.  :-D and :( 

Thinking about migrating it to another family member and moving myself to an mps player that supports ogg...

Thanks.

---

