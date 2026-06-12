---
title: "Comprehensive fix for upside-down webcam?"
date: 2011-04-30
forum: Multimedia Software
---

### Post by Worp8d on 2011-04-30
I've got the upside-down webcam issue in my Asus laptop.  I've fixed the problem for Skype by following the solution in [this]("http://ubuntuforums.org/showthread.php?t=1722963&highlight=webcam+upside+-skype") thread, but the problem persists for Google Video Chat, and anything else that might require a webcam.  I would like a way to permanently fix this problem (rather than just finding a solution for GVC etc.)

The command to start skype is
```
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so QT_PLUGIN_PATH=/usr/lib32/qt4/plugins /usr/bin/skype "$@"
```

The QT_PLUGIN_PATH variable is easy - just set that in /etc/environment and it's sorted.  LD_PRELOAD is more difficult however.  It's a variable(?) that loads a shared library at run-time - "interposing a library".

Is there a way to set the LD_PRELOAD command/variable every time the camera is accessed?

---

