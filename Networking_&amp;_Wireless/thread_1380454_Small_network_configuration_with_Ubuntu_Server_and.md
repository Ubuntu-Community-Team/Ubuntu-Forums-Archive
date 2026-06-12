---
title: "Small network configuration with Ubuntu Server and mixed clients"
date: 2010-01-13
forum: Networking &amp; Wireless
---

### Post by pr0fess0r on 2010-01-13
Hi Guys

For a number of years I've been running our office network which consist of the following:
Wired DSL router
Ubuntu 9.10 Server
1 Windows 7 machine
1 Windows XP Home machine
2 Macs running Snow Leopard
1 Mac running Snow Leopard (wireless via Airport Extreme)
Ps3/Xbox360/AppleTV/Airport Extreme
MacBook Pro running Snow Leopard (wireless via Airport Extreme)

The server holds all our business files and runs Apache, and it's our web development machine.
Our router has the IP 192.168.0.1, the server 192.168.0.2 and the rest of the machines have various 192.168.0.xxx addresses. We use Google DNS 8.8.8.8/8.8.4.4
I manually add 192.168.0.2 <servername> to the /etc/hosts of all the macs

We always have little problems with the network - one of the Snow Leopard macs can create but not rename shared folders on the Ubuntu Samba Share, the XP Home machine needs me to log in to access the Samba share every time it's rebooted, etc

I'm wondering if it's time to go to DHCP, whether I should be using WINS etc. Does anyone have an example configuration for such a network that's reliable and robust? Or any suggestions on a better way to configure such a network?

Many thanks in advance

Lucas

---

