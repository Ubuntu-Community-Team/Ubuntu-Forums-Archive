---
title: "Installed wicd but it wont start from d-bus"
date: 2013-06-02
forum: Networking &amp; Wireless
---

### Post by Nolix on 2013-06-02
I had downloaded wicd and purged and network-manager and network-manager-gnome. on restart it asks for password, I enter it and it says it fails to load d-bus. so far nothing's helped. I've already tried 
[FONT=Verdana]# dpkg-reconfigure wicd
# update-rc.d wicd defaults

it tells me the file in init.d already exists so I dunno what to do.
[/FONT]

---

### Post by praseodym on 2013-06-03
Did you choose your interface name (e.g. wlan0) and "wext" as driver?

---

