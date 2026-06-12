---
title: "Ubuntu 8.04 to recieve an IP address at boot"
date: 2010-03-04
forum: Networking &amp; Wireless
---

### Post by Living2007 on 2010-03-04
How do I make Ubuntu 8.04 receive an IP address as the machine is booting up, so I can access the machine through SSH without having to log in on the X Session.

---

### Post by kiranmurari on 2010-03-04
Hi,

Assuming you have configured your network interface to obtain an ip address through DHCP and if it is an enterprise network, you can talk to your network administrator, so that the DHCP server is configured to assign the same ip whenever a request comes from your machine.
   
If not, you can configure your network interface with a static ip, so that you need not login to X session, to find the IP address. The following link might be helpful.
[http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html)
   
Hope this helps.

---

### Post by Iowan on 2010-03-04
Are you using Network Manager to get an address? NM configures interfaces at login - so setting up the interface via */etc/network/interfaces* might solve your problem...

---

