---
title: "Select network interfaces config at startup or some alternative?"
date: 2011-04-29
forum: Networking &amp; Wireless
---

### Post by Hawkoon on 2011-04-29
I have a couple of interfaces config files, one for home where I use a manually managed static lan connection, and one for the office for system managed DHCP lan.

Currently I copy the one I need after booting up. So when I go to my office I boot up, copy the „office config“ file but then I have to reboot again to get the DHCP connection working. Just restarting the network (/etc/init.d/networking restart) doesn't do the trick.

So I am looking for a way to use a new interfaces file without having to reboot the system, or maybe there is some way to choose a interfaces config file during startup?

Any pointers are appreciated :)

~H

---

