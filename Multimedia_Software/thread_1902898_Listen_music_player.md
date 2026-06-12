---
title: "Listen music player"
date: 2012-01-01
forum: Multimedia Software
---

### Post by Sifro on 2012-01-01
Hello,

I installed "LIsten" music player, and when i run it, i get this error:

> Traceback (most recent call last):
  File "listen", line 213, in <module>
    ListenApp()
  File "listen", line 131, in __init__
    self.listen_instance = Listen()
  File "/usr/lib/listen/widget/listen.py", line 135, in __init__
    self.notify = Notify(self.tray)
  File "/usr/lib/listen/widget/notify.py", line 53, in __init__
    if utils.dbus_service_available(bus,interface,True):
  File "/usr/lib/listen/utils.py", line 92, in dbus_service_available
    bus.start_service_by_name(interface)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 281, in start_service_by_name
    'su', (bus_name, flags)))
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 630, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.Notifications was not provided by any .service files


ANy ideas?
Thanks!

---

### Post by Sifro on 2012-01-05
up =)

---

### Post by be4truth on 2012-02-13
> **Sifro said:**
> up =)

Could you document what you did? Thx

---

