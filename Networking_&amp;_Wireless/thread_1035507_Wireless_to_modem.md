---
title: "Wireless to modem"
date: 2009-01-09
forum: Networking &amp; Wireless
---

### Post by krzysz00 on 2009-01-09
I am trying to install Debian on an old laptop whose CD drive isn't working well. The laptop has a D-Link DWL-650 which needs hostap to work. The laptop also has a port for a dila-up cable. I also have a desktop, running Ubuntu 8.10 with a wireless card, which provides my Internet connection, and an unused Ethernet card and modem. I was thinking to use a Debian boot floppy and connect the laptop and desktop with PPP cable and use the wireless Internet on the desktop to install Debian on the laptop. How would I go about this, or should I try a different approach? (Am perfectly fine with terminal)

---

### Post by krzysz00 on 2009-01-10
<bump>Hello</bump>

---

### Post by cdtech on 2009-01-10
You should be able to turn on IP forwarding and set the laptop to use the desktop as its default route. Then just masquerade anything going out the ppp0 interface (iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE). Here is the method to enable IP forwarding:
[http://www.ducea.com/2006/08/01/how-to-enable-ip-forwarding-in-linux/](http://www.ducea.com/2006/08/01/how-to-enable-ip-forwarding-in-linux/)

---

### Post by ieee488 on 2009-01-10
If you have a serial port on both PCs, see if 
[http://howto.gumph.org/content/xp-direct-cable-to-linux/](http://howto.gumph.org/content/xp-direct-cable-to-linux/)
will help. It is for XP to Linux; though you should be able to get Linux to Linux working.

Then, on one of the PC, set up vsftpd.
[http://ubuntuforums.org/archive/index.php/t-91887.html](http://ubuntuforums.org/archive/index.php/t-91887.html)

I got it working between XP Home and Ubuntu 8.04.

---

