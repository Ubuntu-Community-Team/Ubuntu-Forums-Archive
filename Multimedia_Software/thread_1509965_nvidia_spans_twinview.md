---
title: "nvidia spans twinview"
date: 2010-06-14
forum: Multimedia Software
---

### Post by WamBamBoozle on 2010-06-14
Once upon a time I could double click a playing movie and it would fill the nearest monitor in my twinview setup. Now, my system is pretending that the two monitors make one very wide monitor. I prefer the old behavior.

I have two 1980x1080 or whatever they're called.

Its a fresh install of Lucid running nvidia on a 2 or 3 year old dual core AMD. 64 bit.

I believe the terminology is "nvidia spans twinview" but I could be wrong.

One thing I notice is that the nvidia control applet is having problems. For example, when logged in as root and literally removing /etc/X11/xorg.conf, I get the following sad diagnostics in my root console

```

root@zzz:/etc/X11# mv xorg.conf{,.sv}
root@zzz:/etc/X11# nvidia-settings 
Traceback (most recent call last):
  File "/usr/share/screen-resolution-extra/nvidia-polkit.py", line 75, in <module>
    operation_status = main(options)
  File "/usr/share/screen-resolution-extra/nvidia-polkit.py", line 42, in main
    conf = get_xkit_service()
  File "/usr/share/screen-resolution-extra/nvidia-polkit.py", line 33, in get_xkit_service
    service_object = dbus.SystemBus().get_object(SERVICE_NAME, OBJECT_PATH)
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
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.PermissionsInvalid: The permission of the setuid helper is not correct

ERROR: Unable to open X config file '/etc/X11/xorg.conf' for writing.

```

I suspect nvidia drivers are broken.

---

