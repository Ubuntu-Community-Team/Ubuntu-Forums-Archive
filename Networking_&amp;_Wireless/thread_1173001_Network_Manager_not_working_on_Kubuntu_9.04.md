---
title: "Network Manager not working on Kubuntu 9.04"
date: 2009-05-29
forum: Networking &amp; Wireless
---

### Post by jhahoneyk on 2009-05-29
I'm running Kubuntu 9.04 with all updates applied. Network Manager - Plasma applet always says "connection failed" whether its a static eth connection, or a ppp connection through my phone. All work fine in ubuntu.
Currently, I have to manually run ifconfig, route and update /etc/resolv.conf .
I tried to use nm-applet on kubuntu, but it shows my wired connection as "not managed". I have created a wired config in NetworkManager settings, both in KDE Settings and nm-applet settings. Any ideas whats wrong?

---

### Post by automaton26 on 2009-05-29
I've had nothing but problems with NetworkManager under Kubuntu 8.10 and 9.04 - I prefer to use a static IP.

So, the first thing I do is manually configure the network, install **wicd** and finally remove NetworkManager.

---

### Post by Iowan on 2009-05-29
Check */etc/network/interfaces*. NM won't manage interfaces defined there.  Ordinarily, only "lo" is defined there... at least on Ubuntu.

---

