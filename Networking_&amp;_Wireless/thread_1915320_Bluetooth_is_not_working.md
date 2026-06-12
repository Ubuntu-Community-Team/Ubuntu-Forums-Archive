---
title: "Bluetooth is not working"
date: 2012-01-26
forum: Networking &amp; Wireless
---

### Post by Animeltu on 2012-01-26
Hello, 
I tried to google my problem, however, my attempts were unsuccessful, for some reason bluetooth on my laptop just stopped working and error code which Bluethooth Manager gives me is: 

 Network is down
Traceback (most recent call last):
  File "/usr/bin/blueman-manager", line 231, in inquiry
    self.List.DiscoverDevices()
  File "/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py", line 445, in DiscoverDevices
    self.Adapter.StartDiscovery()
  File "/usr/lib/python2.7/dist-packages/blueman/bluez/utils.py", line 28, in warp
    raise errors.parse_dbus_error(exception)
DBusFailedError: Network is down


any ideas?

---

