---
title: "Exaile w/gstreamer equailzer"
date: 2007-07-09
forum: Multimedia &amp; Video
---

### Post by louis077 on 2007-07-09
I spent a good hour getting the latet gst-plugins-bad (cvs16052007) to compile in Feisty and now when I try and enable the equalizer in Exaile I still get the same error that its not available.  Here is the output from 'gst-inspect equalizer'

```
   
  Name:                 equalizer
  Description:          GStreamer audio equalizers
  Filename:             /usr/local/lib/gstreamer-0.10/libgstequalizer.so
  Version:              0.10.5
  License:              LGPL
  Source module:        gst-plugins-bad
  Binary package:       GStreamer Bad Plug-ins source release
  Origin URL:           Unknown package origin

  equalizer-10bands: 10 Band Equalizer
  equalizer-3bands: 3 Band Equalizer
  equalizer-nbands: N Band Equalizer

  3 features:
  +-- 3 elements

```


Does anyone have any suggestions?

-----EDIT-----

I installed some debs and recompiled and for some weird reason it works!

---

