---
title: "Real time playback sound effects"
date: 2010-04-18
forum: Multimedia Software
---

### Post by dE_logics on 2010-04-18
Is there any ALSA plugin or audio player which provides real time sound effects (for e.g. low frequency amplification, surround etc...)?

---

### Post by dE_logics on 2010-04-19
No one knows?

---

### Post by Yellow Pasque on 2010-04-19
foobar2000 through WINE ;)
Also, there are dsp plugins for ladspa/slv2, but I don't know what audio player uses them. Ubuntu doesn't even compile gstreamer with slv2.

---

### Post by dE_logics on 2010-04-20
You mean these - 

```
* media-plugins/gst-plugins-ladspa
     Available versions:  (0.10) 0.10.14!t 0.10.17!t
     Homepage:            http://gstreamer.freedesktop.org/
     Description:         plugin for gstreamer

* media-plugins/ladspa-bs2b
     Available versions:  ~0.9.1
     Homepage:            http://bs2b.sourceforge.net/
     Description:         LADSPA plugin for bs2b headphone filter
```

You tried compiling?

ladspa-bs2b in the Ubuntu repos. I'll look forward to this. Thanks!

---

