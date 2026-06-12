---
title: "Connecting to the internet without nm-applet?"
date: 2012-12-28
forum: Networking &amp; Wireless
---

### Post by kerryhall on 2012-12-28
I recently changed my window manager from metacity to fluxbox. I forgot to add nm-applet to my ~/.fluxbox/startup file, and I can confirm that it is not running, but somehow I'm connected to the internet.

What is going on there? Thanks! (12.04)

---

### Post by steeldriver on 2012-12-28
The nm-applet is only a front end - the network-manager service is probably still running behind the scenes and will read and setup your default connection from /etc/NetworkManager/system-connections/

You can check with

```
service network-manager status
```or use the command line nm-tool to see device / connection details

Either that or you have a connection defined using the older networking service (via /etc/network/interfaces)

---

### Post by kerryhall on 2013-01-04
Ah awesome, thanks for the help on this!!

---

