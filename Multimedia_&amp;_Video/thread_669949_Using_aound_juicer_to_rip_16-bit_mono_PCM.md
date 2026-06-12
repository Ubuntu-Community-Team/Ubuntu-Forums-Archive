---
title: "Using aound juicer to rip 16-bit mono PCM"
date: 2008-01-16
forum: Multimedia &amp; Video
---

### Post by niglch on 2008-01-16
Is there any way to use sound juicer to rip to mono 16-bit 44100kHz WAV format? I went to preferences and made a new audio profile with the following gstreamer pipeline:
```
audio/x-raw-int,rate=44100,channels=1 ! wavenc name=enc
```
However, this output a 25-bit file which I can't use with a multitracker device I have. How do I force the file to be 16-bit?

---

### Post by morgan_greywolf on 2008-01-17
Have you tried the [GStreamer Pipeline Editor](http://gstreamer.freedesktop.org/modules/gst-editor.html) (gst-editor)?

Worst case, you can always take the 25-bit files which you can then edit it something like Audacity and use that to convert them to 16-bit files.  This can be cumbersome if you have a lot of files, though.

---

