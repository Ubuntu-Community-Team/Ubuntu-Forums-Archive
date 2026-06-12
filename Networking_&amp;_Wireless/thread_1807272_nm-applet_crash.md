---
title: "nm-applet crash"
date: 2011-07-18
forum: Networking &amp; Wireless
---

### Post by insanekat on 2011-07-18
Somewhat randomly, my nm-applet will crash and I will obviously lose all internet on 11.04. I have used the temporary fix of opening a terminal and simply running nm-applet, however I was hoping for an actual fix if anyone knows of one?

Here's what shows up in the terminal once I run nm-applet:

```
** (nm-applet:17377): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:17377): DEBUG: foo_client_state_changed_cb

** (nm-applet:17377): WARNING **: _nm_object_get_property: Error getting 'Flags' for /org/freedesktop/NetworkManager/AccessPoint/35: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:17377): WARNING **: _nm_object_get_property: Error getting 'WpaFlags' for /org/freedesktop/NetworkManager/AccessPoint/35: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:17377): WARNING **: _nm_object_get_property: Error getting 'RsnFlags' for /org/freedesktop/NetworkManager/AccessPoint/35: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:17377): WARNING **: _nm_object_get_property: Error getting 'WpaFlags' for /org/freedesktop/NetworkManager/AccessPoint/34: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:17377): WARNING **: _nm_object_get_property: Error getting 'RsnFlags' for /org/freedesktop/NetworkManager/AccessPoint/34: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:17377): WARNING **: _nm_object_get_property: Error getting 'WpaFlags' for /org/freedesktop/NetworkManager/AccessPoint/33: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:17377): WARNING **: _nm_object_get_property: Error getting 'RsnFlags' for /org/freedesktop/NetworkManager/AccessPoint/33: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:17377): WARNING **: _nm_object_get_property: Error getting 'WpaFlags' for /org/freedesktop/NetworkManager/AccessPoint/32: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:17377): WARNING **: _nm_object_get_property: Error getting 'RsnFlags' for /org/freedesktop/NetworkManager/AccessPoint/32: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:17377): WARNING **: _nm_object_get_property: Error getting 'WpaFlags' for /org/freedesktop/NetworkManager/AccessPoint/31: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:17377): WARNING **: _nm_object_get_property: Error getting 'RsnFlags' for /org/freedesktop/NetworkManager/AccessPoint/31: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:17377): WARNING **: _nm_object_get_property: Error getting 'WpaFlags' for /org/freedesktop/NetworkManager/AccessPoint/30: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:17377): WARNING **: _nm_object_get_property: Error getting 'RsnFlags' for /org/freedesktop/NetworkManager/AccessPoint/30: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:17377): WARNING **: _nm_object_get_property: Error getting 'WpaFlags' for /org/freedesktop/NetworkManager/AccessPoint/29: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:17377): WARNING **: _nm_object_get_property: Error getting 'RsnFlags' for /org/freedesktop/NetworkManager/AccessPoint/28: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:17377): WARNING **: _nm_object_get_property: Error getting 'WpaFlags' for /org/freedesktop/NetworkManager/AccessPoint/27: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:17377): WARNING **: _nm_object_get_property: Error getting 'RsnFlags' for /org/freedesktop/NetworkManager/AccessPoint/24: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:17377): WARNING **: _nm_object_get_property: Error getting 'RsnFlags' for /org/freedesktop/NetworkManager/AccessPoint/23: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist


** (nm-applet:17377): DEBUG: foo_client_state_changed_cb

```

---

### Post by byronpdx on 2011-08-14
I am having the same error. It appears that Ubuntu is going downhill fast. The new interface is just bad, the number of things that don't work is getting more and more, and now the applets have stopped working or are not available anymore.

Does anyone know how to fix this?

What is happening with Ubuntu? Is it dying? :(

---

