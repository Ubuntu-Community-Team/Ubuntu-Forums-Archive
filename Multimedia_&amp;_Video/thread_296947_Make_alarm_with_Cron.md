---
title: "Make alarm with Cron"
date: 2006-11-10
forum: Multimedia &amp; Video
---

### Post by gottferdamnt on 2006-11-10
Hi! 

I tried to configure crontab to play a musics playlist with Exaile; but when my shell script is running with cron, I get this error message in my Cron log:

```
Traceback (most recent call last):
  File "/usr/share/exaile/xl/dbusinterface.py", line 203, in test
    bus = dbus.SessionBus()
  File "/var/lib/python-support/python2.4/dbus/_dbus.py", line 266, in __new__
    return Bus.__new__(cls, Bus.TYPE_SESSION, use_default_mainloop, private)
  File "/var/lib/python-support/python2.4/dbus/_dbus.py", line 99, in __new__
    bus._connection = dbus_bindings.bus_get(bus_type, private)
  File "dbus_bindings.pyx", line 1692, in dbus_bindings.bus_get
DBusException: Unable to determine the address of the message bus (try 'man dbus-launch' and 'man dbus-daemon' for help)
No running Exaile instance found.
```

Otherwise my script works well when I use it without cron. 

Any idea? 

thx.

---

