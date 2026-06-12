---
title: "wireless unmanaged, need edit config, bug?"
date: 2009-04-21
forum: Networking &amp; Wireless
---

### Post by mvdberg112 on 2009-04-21
[http://ubuntuforums.org/showthread.php?p=5926426](http://ubuntuforums.org/showthread.php?p=5926426)
In the nm-applet, my devices were unmanaged after upgrading to 8.10. It was not possible to set them to managed. Actually, there is not interface in the new applet to add or remove an interface from the NetworkManager.

As suggested, edit:
 /etc/NetworkManager/nm-system-settings.conf 
this line ```
[ifupdown]
managed=false
```change into
```
[ifupdown] to 
managed=true
```and also in /etc/network/interfaces remove or comment out the lines:
```
iface wlan0
```Now my WLAN0 is managed by the applet.

Why is this?
Is this a bug?

---

