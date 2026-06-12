---
title: "Spotify song notifications using notify-osd"
date: 2009-10-28
forum: Multimedia Software
---

### Post by SveinT on 2009-10-28
Hi,

recently I created a python script called spotify-notify, which displays song notifications of currently playing song in Spotify using notify-osd and info from last.fm.

I hope you'll check it out if you're interested and give some feedback :)

You can find it here:
[http://code.google.com/p/spotify-notify/](http://code.google.com/p/spotify-notify/)

---

### Post by matzino on 2009-11-01
its great thank you

---

### Post by Maelstrome26 on 2010-06-01
Brilliant idea! If there was a way to set it so that it starts upon boot, that would be even better! :-)

---

### Post by alexandrius on 2011-02-11
Doesn't work for me:
```
alexander@alex:~/Desktop$ python spotify-notify.py 
Spotify-notify v0.5.2
Connecting
Traceback (most recent call last):
  File "spotify-notify.py", line 143, in <module>
    SN = SpotifyNotify()
  File "spotify-notify.py", line 26, in __init__
    self.connect()
  File "spotify-notify.py", line 32, in connect
    self.spotifyservice = self.bus.get_object('com.spotify.qt', '/org/mpris/MediaPlayer2')
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 244, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 241, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 183, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 281, in start_service_by_name
    'su', (bus_name, flags)))
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 620, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name com.spotify.qt was not provided by any .service files
```

any ideas?

---

### Post by IraGainesUK on 2011-03-11
That's because you're using a version that doesn't support using Spotify through WINE.  The last version of spotify-notify that supports Spotify through WINE is v0.1.1, grab it here:

[http://code.google.com/p/spotify-notify/downloads/list](http://code.google.com/p/spotify-notify/downloads/list)

It's old, but still works! (I'm using it now).

---

### Post by scooby359 on 2011-06-18
Just to be a lil awkward, but would this work in Lubuntu? And if not, is there any easy way of making it?

---

