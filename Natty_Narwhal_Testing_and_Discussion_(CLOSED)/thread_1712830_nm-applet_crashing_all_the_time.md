---
title: "nm-applet crashing all the time"
date: 2011-03-23
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by sonicb00m on 2011-03-23
My nm-applet is crashing and leaving the network unusable until i relaunch it.

If i relaunch it with the terminal it runs ok until the next crash


** (nm-applet:9828): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:9828): DEBUG: foo_client_state_changed_cb
** (nm-applet:9828): DEBUG: foo_client_state_changed_cb

** (nm-applet:9828): WARNING **: _nm_object_get_property: Error getting 'RsnFlags' for /org/freedesktop/NetworkManager/AccessPoint/69: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



It's a clean install from just a few days ago and updated to the current packages.

---

### Post by ronacc on 2011-03-23
Is it actually crashing and generating a crash report or just disconnecting ? I have both problems on my system , 64bit and rtl8185 . there are bug reports for both . if it is always generating a crash report see and join Bug 729150 , if it sometime (or always ) disconnects with no bug report and the Icon still there see and join Bug 726058 . if you have both problems join both .

---

