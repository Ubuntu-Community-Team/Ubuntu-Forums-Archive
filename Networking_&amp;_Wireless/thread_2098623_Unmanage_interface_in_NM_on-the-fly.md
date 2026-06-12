---
title: "Unmanage interface in NM on-the-fly ?"
date: 2012-12-27
forum: Networking &amp; Wireless
---

### Post by Grawp on 2012-12-27
Hi

Is it possible to mark a normally managed interface in NetworkManager as non-managed without adding it to /etc/network/interfaces and restarting network-manager?
I very often need to disable managing on some interface + it's not even the same interface that I need to disable managing of every time. One time it's eth0, other time it's wlan0 or wlan1.
Is there some D-BUS command or something that I can utilize to reach my goal?

---

### Post by steeldriver on 2012-12-27
I've been trying to do some basic dbus stuff myself recently and am finding VERY frustrating - the nearest I can get for your query is

```
$ dbus-send --print-reply --system --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.NetworkManager.GetDeviceByIpIface string:"wlan0"
method return sender=:1.5 -> dest=:1.216 reply_serial=2
   object path "/org/freedesktop/NetworkManager/Devices/1"
$ 
$ dbus-send --system --print-reply --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager/Devices/1 org.freedesktop.DBus.Properties.Get string:"org.freedesktop.NetworkManager.Device" string:"Managed"
method return sender=:1.5 -> dest=:1.218 reply_serial=2
   variant       boolean true
$ 
$ sudo dbus-send --system --print-reply --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager/Devices/1 org.freedesktop.DBus.Properties.Set string:"org.freedesktop.NetworkManager.Device" string:"Managed" variant:boolean:false
[sudo] password for steeldriver: 
Error org.freedesktop.DBus.Error.AccessDenied: Property "Managed" of interface "org.freedesktop.NetworkManager.Device" is not settable
$ 

```

Good luck and pls post back if you manage to make it work!

---

