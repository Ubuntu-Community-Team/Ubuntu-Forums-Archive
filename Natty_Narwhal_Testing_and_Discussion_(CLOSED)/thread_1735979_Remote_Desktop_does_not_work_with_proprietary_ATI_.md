---
title: "Remote Desktop does not work with proprietary ATI FGLRX driver"
date: 2011-04-22
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by memorygap on 2011-04-22
I installed the proprietary ATI drivers and then set up remote desktop. The client can connect and interact with the VNC server  but receives no screen updates.
I confirmed that this issue does not occur with the drivers removed.
Perhaps the user should be notified when enabling remote desktop when they have the drivers installed that it may not work correctly?

---

### Post by ubername on 2011-04-22
I don't think the problem is specific to the ATI drivers, rather to using VNC with desktop effects enabled.


1) Open a terminal or press ALT+F2, then run/type: gconf-editor
 2) Go to /desktop/gnome/remote_access and enable "disable_xdamage"

 Allows VNC without disabling desktop effects.

[http://ubuntuforums.org/showpost.php...8&postcount=14](http://ubuntuforums.org/showpost.php...8&postcount=14)

---

