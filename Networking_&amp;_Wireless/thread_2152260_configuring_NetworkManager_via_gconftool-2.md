---
title: "configuring NetworkManager via gconftool-2"
date: 2013-06-07
forum: Networking &amp; Wireless
---

### Post by davidmaxwaterman on 2013-06-07
I tried to add some routes to a connection in NetworkManager using :

$ gconftool-2 --type list --list-type int --set /system/networking/connections/1/ipv4/routes "[....]"

but it didn't change anything in NetworkManager. If I :

$ gconftool-2 --recursive-list /system/networking/connections/1/ipv4

it does show that it's changed. If I look in ~/.gconf, it seems not to reflect what is in Network Manager (using the nm-applet).

What am I missing?

I'm using 13.04, fwiw

---

### Post by davidmaxwaterman on 2013-06-10
does anyone have any ideas on the above?

---

