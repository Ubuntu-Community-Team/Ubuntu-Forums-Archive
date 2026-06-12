---
title: "[SOLVED] Nicotine calls Gstreamer?"
date: 2008-01-26
forum: Multimedia &amp; Video
---

### Post by twiggyness2000 on 2008-01-26
I uninstalled gstreamer a short while ago in favor of xine which plays my media quite nicely.  Now nicotine won't run...a blank window appears with "nicotine+ 1.2.8" in the title bar.
Here is the output when run from CLI:

```
~$ nicotine
Nicotine supports a country code blocker but that
        requires a (GPL'ed) library called GeoIP. You can find it here:
        C library:       http://www.maxmind.com/app/c
        Python bindings: http://www.maxmind.com/app/python
        (the python bindings require the C library)

Traceback (most recent call last):
  File "/usr/bin/nicotine", line 156, in <module>
    app = frame.MainApp(config, trayicon)
  File "/var/lib/python-support/python2.5/pynicotine/gtkgui/frame.py", line 2230, in __init__
    self.frame = NicotineFrame(config, trayicon)
  File "/var/lib/python-support/python2.5/pynicotine/gtkgui/frame.py", line 402, in __init__
    self.gstreamer = gstreamer()
  File "/var/lib/python-support/python2.5/pynicotine/gtkgui/frame.py", line 2208, in __init__
    self.player = gst.element_factory_make("playbin", "player")
gst.ElementNotFoundError: playbin
```

Can I install a single package to satisfy the program or do i HAVE to have gstreamer to run nicotine+  --   or is there a way to circumnavigate?  This is all assuming Gstreamer is the problem -- I checked the website and it *appears* gstreamer is called upon for sound playback(which NEVER worked for me anyway)

thnx in advance

---

### Post by marioquark on 2008-02-04
i have the same problem. any suggestion?

---

### Post by marioquark on 2008-02-04
SOLVED:
just install **gstreamer0.10-plugins-base** that contains playbin...

---

### Post by chochem on 2008-03-10
thanks for the tip, marioquark.

strange that this isn't noted as a dependency, then?

---

