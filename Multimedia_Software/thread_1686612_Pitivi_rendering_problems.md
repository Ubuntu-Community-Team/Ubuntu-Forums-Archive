---
title: "Pitivi rendering problems"
date: 2011-02-12
forum: Multimedia Software
---

### Post by mpnordland on 2011-02-12
Hi, After reading a lot, updating gstreamer from the ppa, and trying the development version, I still have this one show stopping problem with pitivi: It won't render. I've tried the moving the timeline cursor, using different quality/codec/resolution settings, and still no dice. I was able to get a previous version to render by splitting it into three sections, and then when I presented it, I used a playlist and totem to play them one after the other, that was usable, but there was one spelling mistake, and there were some problems at the junctions of the individual rendered clips. So I wanted to do a new version that was better put together for being split, and correct that misspelled word, and, since I had moved files around since rendering, none my project files would work, so I re-edited the whole thing, which fortunately didn't take too long, and now I got the first section to render, but for the rest, I'm stuck. I have to do this presentation tomorrow, and I still have the first version, but I would like to have this improved version done and ready. The project is made up of mostly pictures some videos. Help would be appreciated.

---

### Post by cotcot on 2011-02-12
Maybe [this thread ]("http://ubuntuforums.org/showthread.php?t=1478028")could help you (if you do not have seen it yet of course).

You do not tell something about error messages. Start pitivi in terminal and check if it throws any useful errors during rendering.

---

### Post by mpnordland on 2011-02-12
ahh, I'd just loaded the page to add such output. and here it is


```
ERROR [25483] [0x   -48b0e940] "<Pipeline at 0x971b80c>"        pipeline          Feb 12 17:03:11      _errorObject: error from /GstPipeline:pipeline1/GstBin:bin51/GstAutoVideoSink:autovideosink2/GstXvImageSink:autovideosink2-actual-sink-xvimage (__main__.GstXvImageSink): Internal GStreamer error: negotiation problem.  Please file a bug at http://bugzilla.gnome.org/enter_bug.cgi?product=GStreamer. (xvimagesink.c(2253): gst_xvimagesink_setcaps (): /GstPipeline:pipeline1/GstBin:bin51/GstAutoVideoSink:autovideosink2/GstXvImageSink:autovideosink2-actual-sink-xvimage:
Error calculating the output display ratio of the video.) (/usr/lib/pitivi/python/pitivi/log/loggable.py:30)
ERROR [25483] [0x   -48b0e940] "<Pipeline at 0x971b80c>"        pipeline          Feb 12 17:03:11      _errorObject: error from /GstPipeline:pipeline1/GstBin:bin1/GnlComposition:gnlcomposition2/GnlSource:gnlsource: VideoTestSourceFactory43/GstBin:bin45/GstVideoTestSrc:videotestsrc12 (__main__.GstVideoTestSrc): GStreamer encountered a general stream error. (gstbasesrc.c(2574): gst_base_src_loop (): /GstPipeline:pipeline1/GstBin:bin1/GnlComposition:gnlcomposition2/GnlSource:gnlsource: VideoTestSourceFactory43/GstBin:bin45/GstVideoTestSrc:videotestsrc12:
streaming task paused, reason not-negotiated (-4)) (/usr/lib/pitivi/python/pitivi/log/loggable.py:30)
```
also, I've read that and tried that, and it doesn't work :(

---

### Post by mpnordland on 2011-02-12
another thing is that pitivi throws the most useless error messages I've ever seen, for me anyway, do you think if I compiled and installed the absolute latest gstreamer it would make a difference?

---

### Post by kiddo on 2011-02-12
Developers don't read forums. What you are seeing is a bug and you should file bug reports instead of posting on forums, so that your issue can be investigated properly.

---

### Post by mpnordland on 2011-02-12
Ok, I found out on IRC that there is a bug filed for this already, but
just one question, can I use my ubuntu forums account to post bugs?

---

