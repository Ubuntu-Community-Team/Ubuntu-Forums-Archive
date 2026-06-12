---
title: "Exaile Problems"
date: 2007-11-28
forum: Multimedia &amp; Video
---

### Post by koulanji on 2007-11-28
So I still have my problems with exaile {the same terminal error to be exact} and this is an error that I get after I have reinstalled and cleaned the system multiple times. Does anyone have any idea what this error means

axisaudio@axisaudio-desktop:~$ exaile
Traceback (most recent call last):
  File "exaile.py", line 44, in <module>
    import gtk, gtk.glade, pango, dbus
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
  File "/usr/lib/python2.5/site-packages/cairo/__init__.py", line 1, in <module>
    from _cairo import *
ImportError: /usr/lib/python2.5/site-packages/cairo/_cairo.so: undefined symbol: cairo_clip_extents
axisaudio@axisaudio-desktop:~$ 

What's even weirder is that I get the same exact error in my software sources. Is there any way to resolve this?

---

### Post by imdano on 2007-11-30
This might help: [https://bugs.launchpad.net/libcairo/+bug/129816](https://bugs.launchpad.net/libcairo/+bug/129816)

---

