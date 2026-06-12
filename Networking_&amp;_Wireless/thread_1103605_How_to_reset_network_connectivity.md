---
title: "How to reset network connectivity"
date: 2009-03-22
forum: Networking &amp; Wireless
---

### Post by jcobban on 2009-03-22
Somehow my Internet network connectivity has become corrupted.  I cannot imagine how I could have done this, but that is not the issue.  Ubuntu should just be picking up the information it needs to connect to the outside world from the router, and it did so until this week when it just stopped working.  When I boot from the startup CD it connects to the network.

I think I just have to somehow reset whatever configuration options Ubuntu uses to connect to the Internet to defaults, so it will pick up the settings from the router.  How do I do that?

---

### Post by Iowan on 2009-03-23
Short of re-installing (save that as a VERY last resort), It might be easier to reconfigure your connection.  What is in */etc/network/interfaces*? Results of **ifconfig -a**? The new Network Manager stores it's settings in /etc/NetworkManager - /etc/NetworkManager/nm-system-settings.conf.

---

### Post by jcobban on 2009-03-24
> **Iowan said:**
> Short of re-installing (save that as a VERY last resort), It might be easier to reconfigure your connection.  What is in */etc/network/interfaces*? Results of **ifconfig -a**? The new Network Manager stores it's settings in /etc/NetworkManager - /etc/NetworkManager/nm-system-settings.conf.

Thank you.:D

/etc/network/interfaces contained:

auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual

============================
I don't know why this continued working after I switched from direct connection through a cable modem to connecting through a router.  I deleted the DSL section and changed eth0 to use dhcp and everything works fine now.  In particular I was able to post this message from my Ubuntu system.

---

