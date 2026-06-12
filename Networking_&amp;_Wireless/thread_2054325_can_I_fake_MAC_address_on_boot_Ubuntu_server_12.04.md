---
title: "can I fake MAC address on boot Ubuntu server 12.04.1 LTS"
date: 2012-09-07
forum: Networking &amp; Wireless
---

### Post by mezera on 2012-09-07
Good morning,

I'm new here and not a native speaker, so please bear with me and my English.

What I want to do:
I want to replace my openSUSE server by an Ubuntu server 12.04.1 LTS. My Internet provider does MAC filtering and only distributes DHCP IP addresses if the connecting machine has the MAC address stored in his table.

If have done this long time ago with a Debian server (ifconfig pre-up) and do it on the openSUSE server (LLADDR) now, but have not been able to do it on Ubuntu. For testing purpose I set up virtualBox on my Ubuntu desktop and installed a virtual server there. Than I added hwaddress 01:02:03:04:05:06 to the iface eth0 line in /etc/network/interfaces and commented out the eth0 line in /etc/udev/rules.d/70-persistent-net.rules because changing only the interfaces file did not work as well.

How can I achieve my goal? Please help.

TIA Heinz (from Vienna, Austria)

---

