---
title: "multiple wireless interfaces in ubuntu 9.04? auto/manual?"
date: 2009-09-01
forum: Networking &amp; Wireless
---

### Post by freeballer on 2009-09-01
I have a macbook with the intergrated atheros n wireless card... I also have a realtek rt8180 usb wireless card (b/g). I want to run them both testing kismet - and really no easy way to hook it up via ethernet because the router is far away and all ports are currently used.

So how can I setup either manually or automatically for atheros to use.. say "wlan0" and the realtek to use... say "wlan1"? in ubuntu itself? When both are plugged in realtek takes over wlan0, disconnects me

please and thank you

---

### Post by Iowan on 2009-09-02
Network Manager only seems to manage one interface at a time (my laptop has wired and wireless, but I only use one at a time). You can still set up interfaces via */etc/network/interfaces*, but NM won't manage them.

---

