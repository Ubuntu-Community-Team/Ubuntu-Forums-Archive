---
title: "RT3573 - no wireless networks found"
date: 2012-11-18
forum: Networking &amp; Wireless
---

### Post by smd0665 on 2012-11-18
Hi. I just bought a Belkin N750 wi-fi USB adapter and can't get it working. After following directions I found online, it looks like I have the driver installed, but Wicd is telling me no wireless networks are found.

lsb_release -d: > Ubuntu 12.10

lsusb: > Bus 001 Device 002: ID 050d:1103 Belkin Components F9L1103 N750 DB 802.11abgn 2x3:3 [Ralink RT3573]

iwconfig: > ra0       Ralink STA 

modinfo rt3573sta | grep 1103: >  alias:          usb:v050Dp1103d*dc*dsc*dp*ic*isc*ip*

modprobe rt3573sta, however, returns nothing.

Any suggestions? Thank you.

---

### Post by smd0665 on 2012-11-24
I was able to connect to the local network using commands I found here:
[http://blog.tplus1.com/index.php/2008/06/13/how-to-connect-to-a-wireless-network-from-the-ubuntu-command-line/]("http://blog.tplus1.com/index.php/2008/06/13/how-to-connect-to-a-wireless-network-from-the-ubuntu-command-line/")

Wicd still tells me no local networks are found, but I was able to play a local network game with someone else without any problem. When I try to connect to the Internet, however, the system freezes. Does anyone know what this might be happening?

---

