---
title: "empathy: Internal error ?anyone?"
date: 2010-03-01
forum: Multimedia Software
---

### Post by glasnhost on 2010-03-01
I've installed empathy 2.26.1 +telepathy on ubuntu jaunty 9.04
I try to voice chat hrough google talk. When the other party accept the incoming call I get:

** Message: tf_stream_error: stream error errorno=0 error=Codec negotiation failed: The codec PCMU must have a non-0 clock rate
...
** (empathy:10676): DEBUG: stream 1 (audio) close: close requested by connection manager
...
** Message: Element error: Internal data flow error. -- gstbasesrc.c(2330): gst_base_src_loop (): /GstPipeline:pipeline0/EmpathyGstAudioSrc:empathygstaudiosrc0/GstGConfAudioSrc:gconfaudiosrc0/GstBin:bin6/GstAlsaSrc:alsasrc0:
streaming task paused, reason not-linked (-1)

As a result empathy client is diconnected.
¿Anyone has the same problem?
Any suggestion?

thx

---

### Post by darolu on 2010-03-01
try getting the newest version; Ubuntu disables video/audio chatting in its packages by default so I'd recommend installing using the newest source code (2.29): [http://ftp.acc.umu.se/pub/GNOME/sources/empathy/](http://ftp.acc.umu.se/pub/GNOME/sources/empathy/)

---

