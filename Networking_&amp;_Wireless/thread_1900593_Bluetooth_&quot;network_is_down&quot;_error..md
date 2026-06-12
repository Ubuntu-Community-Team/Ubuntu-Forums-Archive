---
title: "Bluetooth &quot;network is down&quot; error."
date: 2011-12-26
forum: Networking &amp; Wireless
---

### Post by TacticalApe on 2011-12-26
I am trying to search for bluetooth devices, but when i hit the "search" button, a little error at the bottom pops up that says "Network is down." When I hit the button to give me more information, it gives me this:

```
Network is down
Traceback (most recent call last):
  File "/usr/bin/blueman-manager", line 231, in inquiry
    self.List.DiscoverDevices()
  File "/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py", line 445, in DiscoverDevices
    self.Adapter.StartDiscovery()
  File "/usr/lib/python2.7/dist-packages/blueman/bluez/utils.py", line 28, in warp
    raise errors.parse_dbus_error(exception)
DBusFailedError: Network is down
```

---

### Post by TacticalApe on 2011-12-27
*bump*

---

### Post by inobe on 2011-12-27
you have kubuntu.

i don't know if it's mingled with ubuntu, or if it's a full install, nor do i know what kubuntu version it is, not even kde version, the version of blueman, you gotta help us out man ? :D

i guess you can go to system settings> startup and shutdown> service manager> make sure bluedevil and obex are running.

---

### Post by TacticalApe on 2011-12-27
Sorry, it's Ubuntu 11.10 and it didn't come with KDE, I installed it, and it's KDE version 4.7.2. I don't know how to find out what version of Blueman it is... 
Obex and Bluedevil are running.

---

### Post by inobe on 2011-12-27
it looks like a mass of confusion between desktops, kde uses bluedevil, ubuntu uses blueman!

i never recommend running two de's on the same os because of things like this.

how does this work in ubuntu?

---

