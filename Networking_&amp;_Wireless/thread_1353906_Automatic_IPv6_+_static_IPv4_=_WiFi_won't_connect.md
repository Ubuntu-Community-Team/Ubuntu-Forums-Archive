---
title: "Automatic IPv6 + static IPv4 = WiFi won't connect"
date: 2009-12-13
forum: Networking &amp; Wireless
---

### Post by mludd on 2009-12-13
A couple of weeks ago I bought myself a Lenovo Ideapad s10-2 and as planned I installed Linux on it, at first I tried Debian but the installer was having issues with disk labels so I switched to Ubuntu 9.10 and everything seems to be sort of working except for one little thing, IPv6.

When I attempt to enable IPv6 the network manager absolutely refuses to connect to my WAP (using WPA2-PSK).

The setup I have is one where IPv6 addresses are assigned automatically by rtadvd running on a FreeBSD box and it seems to work for every other machine I've got. If I leave IPv6 off connecting works just fine and I can use IPv4 with both static and DHCP-assigned addresses.

I've also seen a few errors about "no IPv6 routers available" and IPv6-related timeouts in /var/log/syslog but I haven't investigated further since this doesn't really seem to be an issue with the network in general (as I stated, it works fine with other machines running Debian, Slackware, FreeBSD 7.x, Mac OS X and Windows Vista).

Another interesting twist is that every now and then during my experimentation I've noticed that the network manager's "Apply" button is greyed out and I can't do anything about it short of removing the connection, rebooting and reconnecting.

Has anyone else experienced anything like this?

/mludd

---

