---
title: "wicd-curses not working (&quot;Curses!&quot; lol)"
date: 2010-09-24
forum: Networking &amp; Wireless
---

### Post by UbuNoob001 on 2010-09-24
```
$ wicd-curses
Can't connect to the daemon, trying to start it automatically...
Traceback (most recent call last):
  File "/usr/share/wicd/curses/wicd-curses.py", line 1022, in <module>
    setup_dbus()
  File "/usr/share/wicd/curses/wicd-curses.py", line 1014, in setup_dbus
    dbus_ifaces = dbusmanager.get_dbus_ifaces()
  File "/usr/lib/pymodules/python2.6/wicd/dbusmanager.py", line 36, in get_dbus_ifaces
    return DBUS_MANAGER.get_dbus_ifaces()
  File "/usr/lib/pymodules/python2.6/wicd/dbusmanager.py", line 62, in get_dbus_ifaces
    if not self._dbus_ifaces: connect_to_dbus()
  File "/usr/lib/pymodules/python2.6/wicd/dbusmanager.py", line 48, in connect_to_dbus
    return DBUS_MANAGER.connect_to_dbus()
  File "/usr/lib/pymodules/python2.6/wicd/dbusmanager.py", line 79, in connect_to_dbus
    proxy_obj = self._bus.get_object("org.wicd.daemon", '/org/wicd/daemon')
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
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name org.wicd.daemon was not provided by any .service files

```

any thoughts? thanks!

---

### Post by chuy_max on 2011-10-01
I had this problem too. You need to run the wicd daemon (I did this in 11.04)

sudo /etc/init.d/wicd start

Then, you can start wicd-curses without problems.

---

