---
title: "synce-gnome problems"
date: 2007-09-09
forum: Multimedia &amp; Video
---

### Post by stolid_agnostic on 2007-09-09
I am following the instructions here: [http://www.synce.org/index.php/Starting_A_Connection](http://www.synce.org/index.php/Starting_A_Connection) to get my T-mobile DASH phone syncing under Linux. It is running Windows Mobile 6.

I have successfully compiled and installed the packages. But I am getting stuck at the starting section: 

[http://www.synce.org/index.php/Connecting_your_Windows_Mobile_2005_device_via_USB_(usb-rndis-lite)#Instructions_for_kernels_.3C_2.6.21]("http://www.synce.org/index.php/Connecting_your_Windows_Mobile_2005_device_via_USB_(usb-rndis-lite)#Instructions_for_kernels_.3C_2.6.21")

And I am currently in this page as a link after it:
[http://www.synce.org/index.php/Starting_A_Connection#Start_synce-gnome]("http://www.synce.org/index.php/Starting_A_Connection#Start_synce-gnome")

When I run:

  python test.py

I get this error message:

> 
Traceback (most recent call last):
  File "test.py", line 120, in <module>
    TestApp()
  File "test.py", line 21, in __init__
    notif_obj = session_bus.get_object("org.freedesktop.Notifications", "/org/freedesktop/Notifications")
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 410, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 230, in __init__
    _dbus_bindings.UInt32(0))
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 169, in __call__
    reply_message = self._connection.send_message_with_reply_and_block(message, timeout)
dbus.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.Notifications was not provided by any .service files


I'm not sure what this means, but I would love some help with how to proceed.

---

### Post by stolid_agnostic on 2007-09-19
any suggestions?

---

