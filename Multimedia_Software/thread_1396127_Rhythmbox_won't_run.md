---
title: "Rhythmbox won't run"
date: 2010-02-01
forum: Multimedia Software
---

### Post by dondiego2 on 2010-02-01
Just in the last few days Rhythmbox and Listen Music Player will not open for some reason.  This is what I get when I try to run them in terminal:

** (rhythmbox:6049): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:6049): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

(rhythmbox:6049): Rhythmbox-WARNING **: Could not import pygtk
ImportError: No module named pygtk
Segmentation fault

and this is what happens with Listen:

Traceback (most recent call last):
  File "listen", line 32, in <module>
    from option_parser import ListenOptionParser
  File "/usr/lib/listen/option_parser.py", line 25, in <module>
    from const import VERSION
  File "/usr/lib/listen/const.py", line 26, in <module>
    import gtk
ImportError: No module named gtk


Any help?  The only thing that might be related is I installed Audacity recently but I don't remember if this happened at the same time.

---

### Post by Stochastic on 2010-02-02
Moved to Multimedia & Video.

---

### Post by kmunro on 2010-02-02
I'm having the same problem with Rhythmbox and Amarok. Error message when Rhythmbox is run in terminal is

** (rhythmbox:5945): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:5945): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect
Segmentation fault

Any ideas appreciated

---

### Post by spoilingmyself on 2010-03-03
try running from a different folder..

---

### Post by Yellow Pasque on 2010-03-03
> ImportError: No module named pygtk
Segmentation fault

```
sudo apt-get install --reinstall python-gtk2
```

---

