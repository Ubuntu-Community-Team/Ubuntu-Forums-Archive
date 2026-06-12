---
title: "Can't run bluez-simple-agent"
date: 2012-07-23
forum: Networking &amp; Wireless
---

### Post by transmition on 2012-07-23
I'm trying to get bluez-simple-agent to run, but alas I am having no luck. I am able to scan with my bluetooth dongle, I've installed python, pygobject, and dbus-python. When I run bluez-simple-agent, I get the following error:

```

    Traceback (most recent call last):
      File "/usr/bin/bluez-simple-agent", line 5, in <module>
        from gi.repository import GObject
    ImportError: No module named gi.repository

```

So I have no module called gi.repository it seems. One thread suggests installing python3-gi, but arch for arm doesn't seem to have this. I've tried reinstalling packages, and removing python3 and leaving python2, but I've had no luck. Anyone have any ideas?

EDIT:
I discovered what went wrong, I needed to install python-gobject and python2-gobject.

---

