---
title: "Exaile equalizer has no effect on sound"
date: 2008-04-23
forum: Multimedia Software
---

### Post by ivotron on 2008-04-23
Hi,

I'm running Xubuntu Hardy Beta and have Exaile 0.2.13 installed. When I click on the 'enable equalizer' checkbox, the sound isn't modified at all. I have tried this with no sound servers, with JACK and lastly I installed PulseAudio since that's Hardy's default on both, Ubuntu and Xubuntu.

Running Exaile on the terminal shows that (apparently) everything is fine:

```
$ exaile
location: /usr/lib/xulrunner-1.9b5/libxpcom.so 
before 3
Exaile 0.2.13
Created db for thread Thread-1
{'Thread-1': <sqlite3.Connection object at 0x874bf20>}
Closed db for thread Thread-1
-----------------------
 __use_gnome ( /usr/share/exaile/xl/xlmisc.py @ 207):
-----------------------
Traceback (most recent call last):
  File "/usr/share/exaile/xl/xlmisc.py", line 227, in __use_gnome
    '/org/gnome/SettingsDaemon')
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 244, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 241, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 183, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 281, in start_service_by_name
    'su', (bus_name, flags)))
  File "/var/lib/python-support/python2.5/dbus/connection.py", line 607, in call_blocking
    message, timeout)
DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SettingsDaemon was not provided by any .service files

Using multimedia keys from: None
Starting scan timer at 25.0
loading tracks...
done loading tracks...
loading songs
Clearing tracks cache
Importing /home/jimenivo/.exaile/saved/playlist0000.m3u
Last playlist loaded
Loading page 0

ReplayGain support initialized.
Equalizer support initialized.
```

So, I don't know what else can be done. Have any one else had this problem?

Thanks much

---

### Post by suw on 2008-05-10
I have the same problem - It's from exaile - fill a bug for it, I'll look on exaile homepage about how to fix this.

---

### Post by suw on 2008-05-10
OK - here's what I found on exaile's bug:

[https://bugs.launchpad.net/exaile/+bug/212522](https://bugs.launchpad.net/exaile/+bug/212522)

They say:
Confirmed: this is because the new version of gstreamer has changed the API for the equalizer. The equalizer currently only works in Gutsy.

so, until someone change equalizer to use the new API - we-re stucked with no EQ.

---

