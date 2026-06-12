---
title: "Exaile problem"
date: 2007-04-10
forum: Multimedia &amp; Video
---

### Post by kg00005 on 2007-04-10
Hi All,

After upgrading Exaile to 0.2.9 on Edgy, it is not starting.

Traceback (most recent call last):
  File "/usr/share/exaile/xl/dbusinterface.py", line 233, in test
    bus = dbus.SessionBus()
  File "/var/lib/python-support/python2.4/dbus/_dbus.py", line 266, in __new__
    return Bus.__new__(cls, Bus.TYPE_SESSION, use_default_mainloop, private)
  File "/var/lib/python-support/python2.4/dbus/_dbus.py", line 99, in __new__
    bus._connection = dbus_bindings.bus_get(bus_type, private)
  File "dbus_bindings.pyx", line 1692, in dbus_bindings.bus_get
DBusException: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Traceback (most recent call last):
  File "/usr/bin/exaile", line 66, in ?
    from xl import *
  File "/usr/share/exaile/xl/tracks.py", line 18, in ?
    import common, media, db, config, trackslist
  File "/usr/share/exaile/xl/media/__init__.py", line 22, in ?
    from xl.media import mpc
  File "/usr/share/exaile/xl/media/mpc.py", line 15, in ?
    mpc_bool_t = ctypes.c_uint8
AttributeError: 'module' object has no attribute 'c_uint8'

Any ideas?

---

### Post by RikoW on 2007-04-12
Hi,

just got exaile_0.2.9 from their web page and installed it by copying the source. Have the same problem.

> **kg00005 said:**
> Hi All,

After upgrading Exaile to 0.2.9 on Edgy, it is not starting.

[...]
  File "/usr/bin/exaile", line 66, in ?
    from xl import *
  File "/usr/share/exaile/xl/tracks.py", line 18, in ?
    import common, media, db, config, trackslist
  File "/usr/share/exaile/xl/media/__init__.py", line 22, in ?
    from xl.media import mpc
  File "/usr/share/exaile/xl/media/mpc.py", line 15, in ?
    mpc_bool_t = ctypes.c_uint8
AttributeError: 'module' object has no attribute 'c_uint8'

Any ideas?

The problem is apparently in the "optional" mpc media module. Quick and dirty fix is to just remove the module (so you can'l play mpc files anymore). My exaile is installed in /usr/local:

```

> cd /usr/local/exaile_0.2.9/xl/
> sudo mv mpc.py mpc.py.save
> sudo rm mpc.pyc

```

Now exaile should start ....

Hope that helps,

                    Riko

---

### Post by kg00005 on 2007-04-12
Hi Riko,

It helped to start Exaile, thanks.
Quite a lot error messages appear in terminal, but works.

Regards,
G

---

### Post by zob on 2007-05-19
Very nice media player. I have the same bug though. It just doesn't start. I tried to remove the mpc codec from the media archive or whatever it is.
Mine was somewhere else than yours:
/usr/share/exaile/xl/media/
It must be the same file however.
Sadly it didn't work for me. I still have the same problem. Anyone...?

EDIT:
I just discovered that none of my installed multimedia player (exept Totem and Audacity) will play anything. Rhythmbox crashes, VLC crashes, Exaile doesn't start. XMMS tells me to check my soundcard configuration (sorry I'm a newbie and I don't know how - and also to check if some other app is using the sound card - ?). It seems something is wrong. But can anyone guide me in the right direction. I might start this as a new thread, 'cause it's not really an exaile problem exclusively.

EDIT 2:
Problem solved. I found out how to force my config to use the right soundcard in stead of automatic selection. Cool. Exaile is nice.

---

### Post by hyperair on 2007-08-08
Here's a tip: Always select ALSA where possible. Avoid OSS sound like poison. By the OSS (Open Sound System), only one application may control the sound card at the same time. At least that's how it is on my computer. Perhaps if my soundcard had hardware mixing it would be different. Anyway, ALSA supports software mixing, so you can have many applications outputting and inputting sound at the same time.

---

