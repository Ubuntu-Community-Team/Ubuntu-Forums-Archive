---
title: "Transmageddon problem"
date: 2011-12-29
forum: Multimedia Software
---

### Post by colmeweb on 2011-12-29
So I have just installed Transmageddon from the software center and it doesn't seem to do anything. Regardless of the source or output format it either just sits there (see picture) or goes to the estimated time bar, but then never does anything. Its version 0.15 and any help would be perfect. 

Thanks

---

### Post by colmeweb on 2011-12-30
Ok, so I tried to run this in 11.10 running live off a flash drive and the same thing happened. Anybody have any ideas?

---

### Post by chiefofthejojos on 2012-01-02
The problem is caused by this bug:

[https://bugs.launchpad.net/ubuntu/+source/transmageddon/+bug/847764](https://bugs.launchpad.net/ubuntu/+source/transmageddon/+bug/847764)

---

### Post by colmeweb on 2012-01-04
Thank you.

I couldn't tell if there was a fix for this or not. If there is could you walk me through fixing it?

Thanks again.

---

### Post by chiefofthejojos on 2012-01-04
I wish I knew how to fix it. It seems that there is no workaround at the moment. I'll let you know if I discover anything.

---

### Post by kaine08 on 2012-01-09
I'm having the exact same problem. Please let me know if you find a solution.

---

### Post by satanselbow on 2012-01-09
There is a transmageddon ppa that works on 11.10 - I'll post it when i'm on my box at home ;)

---

### Post by jhunter on 2012-05-21
I'm getting a similar problem. Ever since I upgraded...

Either says GStreamer ran into an error, or claims there's no valid frames before the end of the stream. Decided to run in terminal and got the following error:

```
(transmageddon.py:2600): GStreamer-CRITICAL **: gst_pad_set_caps: assertion `caps == NULL || gst_caps_is_fixed (caps)' failed
GStreamer encountered a general stream error.
qtdemux.c(3891): gst_qtdemux_loop (): /GstPipeline:TranscodingPipeline/GstURIDecodeBin:uridecoder/GstDecodeBin2:decodebin22/GstQTDemux:qtdemux2:
streaming stopped, reason not-negotiated
The stream is of a different type than handled by this element.
gstbaseparse.c(1108): gst_base_parse_sink_eventfunc (): /GstPipeline:TranscodingPipeline/GstEncodeBin:encodebin0/GstH264Parse:h264parse3
The stream is of a different type than handled by this element.
gstbaseparse.c(1108): gst_base_parse_sink_eventfunc (): /GstPipeline:TranscodingPipeline/GstEncodeBin:encodebin0/GstH264Parse:h264parse3

```

---

