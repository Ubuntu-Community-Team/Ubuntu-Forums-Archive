---
title: "3G-internet vs lan"
date: 2010-01-06
forum: Networking &amp; Wireless
---

### Post by Silveri on 2010-01-06
I'm running karmic on a toshiba equium laptop, using primarily gnome as my window manager. I use the gnome default network manager to connect to the internet. My connection is via a 3G modem that's hooked to my computer via a USB port. I also have a router that I can hook with the laptop via an ethernet cable.

The problem is that if I hook the router to the computer, my internet starts working, although the modem connection (at least according to the network manager) is still active and available. If I unhook the cable, the internet works again.

How can I "prioritize" the connections, ie define the USB-access as my internet access and the ethernet port as my LAN access?

---

### Post by puppywhacker on 2010-01-06
In the Network Manger in the right-top the network icon edit the IPv4 settings for your router interface (guess eth0). Under routes is a tick-box that says "use this connection only for resources on this network"

That will stop the interface from becoming the "default gateway" as soon as it goes online. Since it will only connect to ip-addresses in the same range.

On the command line you use the "ip route" or "route" commands to show the default gateway.

---

