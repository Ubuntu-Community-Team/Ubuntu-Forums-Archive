---
title: "Acer Aspire 1690 networking problems!"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by oz457 on 2009-02-18
I have been using ubuntu 8.10 with my acer aspire. 
Except for networking problems, everything is working fine. 
The poblem:
I cannot configure the network card with the settings in 
/etc/networks/interfaces
Whatever I put in there, the network card never gets initializes or is recognized.
The following settings in interfaces file:
auto eth0
iface eth0 inet static
       address 10.0.0.5
       network 10.0.0.0
       netmask 255.255.255.240
       gateway 10.0.0.1
       broadcast 10.0.0.15
       up route add default gw 10.0.0.1
<-- end of file.

When I boot and get into Gnome, there is a small network icon that displays the network is disconnected. 
After each boot, I have to play around with the settings, and with some luck, suddenly after disabling and enabling the network, the 100baseT starts to work.

How can I debug, what can I do. I prefer that the system config makes my network card work, but I have been unsuccessful.

Any idea's?

---

