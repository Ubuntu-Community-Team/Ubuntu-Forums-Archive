---
title: "gnome-lirc-properties"
date: 2013-12-29
forum: Multimedia Software
---

### Post by joshuaos on 2013-12-29
Hello!  I'm trying to get a remote control working, and I just want some kind of graphical interface to help me, as the config files are rather challenging.  There are like three bug reports about the failure of gnome-lirc-properties to work without HAL.  However, in 13.10, there is no package "hal" and no packages I install seem to get it to work, or the error to even change.

```
Traceback (most recent call last):
  File "/usr/bin/gnome-lirc-properties", line 31, in <module>
    gnome_lirc_properties.run(sys.argv[1:], datadir)
  File "/usr/lib/pymodules/python2.7/gnome_lirc_properties/__init__.py", line 59, in run
    return ui.RemoteControlProperties(builder, datadir).run()
  File "/usr/lib/pymodules/python2.7/gnome_lirc_properties/ui/RemoteControlProperties.py", line 53, in __init__
    self.__setup_models()
  File "/usr/lib/pymodules/python2.7/gnome_lirc_properties/ui/RemoteControlProperties.py", line 80, in __setup_models
    self.__hardware_manager = hardware.HardwareManager(receivers_db)
  File "/usr/lib/pymodules/python2.7/gnome_lirc_properties/hardware.py", line 255, in __init__
    self.__hal = self.__bus.get_object(HAL_SERVICE, HAL_MANAGER_PATH)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 241, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 248, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 180, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 278, in start_service_by_name
    'su', (bus_name, flags)))
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.Hal was not provided by any .service files

```

Any help please with getting a remote control to work!

Thanks!

---

