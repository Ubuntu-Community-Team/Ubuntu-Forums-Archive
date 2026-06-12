---
title: "Network connections not showing up"
date: 2010-01-12
forum: Networking &amp; Wireless
---

### Post by Bödvar on 2010-01-12
When I click on the network manager icon next to the date in the upper right corner of my screen, my network connections do not show up. I have added two DSL connections on my laptop (username & password) but it doesn't show up. Everyday I need to use

```
sudo pppoeconf
```

if I wish to connect to the internet.

Both these connections are added in the same way on my Desktop Computer and it shows up on the network manager. One of them is even the default which connects automatically on startup.

Because it's not working I assume network manager is not compatible with my laptop. Are there patches to install or other programs that can easily manage my internet connection?

I'm using Ubuntu 9.10 on a not-so-new laptop.

---

### Post by Iowan on 2010-01-12
Early on, Karmic had problems with PPPOE - dunno if it got fixed. One option might be to run **pppoeconf** from */etc/rc.local* (not something I've done...)

---

### Post by jamere on 2010-01-12
you may need to add the "Notification Area" applet back to the panel. I've had to do this several times to get the NW Mgr back. Just a tad buggy. :D

jim m

---

