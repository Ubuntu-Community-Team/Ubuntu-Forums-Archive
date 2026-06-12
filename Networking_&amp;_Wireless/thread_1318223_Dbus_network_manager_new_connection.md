---
title: "Dbus network manager new connection"
date: 2009-11-07
forum: Networking &amp; Wireless
---

### Post by nasp on 2009-11-07
Hi all, ive been trying to detect when NetworkManager gets a a new connection in order to automate some actions. I've read plenty of examples such as this [one]("http://ubuntuforums.org/showthread.php?t=1027173#3") I and finally came up with that:

```
#!/usr/bin/env python
# -*- coding: utf-8 -*-

import gobject, dbus
from dbus.mainloop.glib import DBusGMainLoop

# what to do on network device activation
def on_device_now_active(*args):
        print "hello"
                #os.system("skype &") # run skype in background

# dbus events will be part of glib message loop
DBusGMainLoop(set_as_default=True)
# attach to D-BUS system bus and wait for DeviceNowActive event
bus = dbus.SystemBus()
proxy = bus.get_object('org.freedesktop.NetworkManager',
        '/org/freedesktop/NetworkManager')
proxy.connect_to_signal("DeviceNowActive", on_device_now_active)
# program main loop - waits for events and dispatches handlers
loop = gobject.MainLoop()
loop.run()
```

and that

```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
import gobject, httplib, pynotify, dbus
from dbus.mainloop.glib import DBusGMainLoop

def new_connection_handler(device):
    print device

NM_DBUS_SERVICE = "org.freedesktop.NetworkManager"
NM_DBUS_OBJECT_PATH = "/org/freedesktop/NetworkManager"
NM_DBUS_INTERFACE = NM_DBUS_SERVICE

DBusGMainLoop(set_as_default=True)

bus = dbus.SystemBus()

bus.add_signal_receiver(new_connection_handler, 'StateChanged', 'org.freedesktop.NetworkManager')

loop = gobject.MainLoop()
loop.run()

```

Which doesn't work at all (I turn my wifi on and off to reconnect but i get no signal trough dbus).

Anyone has an idea why neither approach works?

---

