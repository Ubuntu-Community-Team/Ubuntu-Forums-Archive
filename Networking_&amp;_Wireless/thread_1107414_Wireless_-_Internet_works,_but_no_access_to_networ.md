---
title: "Wireless - Internet works, but no access to network or router"
date: 2009-03-26
forum: Networking &amp; Wireless
---

### Post by zadkeo on 2009-03-26
Edit: Following is my original post. I solved it by disabling eth0. Can I not leave both eth0 and wlan0 enabled at the same time?


I need some help from someone smarter than I am. I used to have my desktop connected via ethernet. Yesterday I installed an Edimax EW-7128G. I started up and was able to access internet through the wireless card. But I cannot access my router configuration page, ping my router, or ping other computers on the network through wireless. I can however get an IP using DHCP.

If I switch back to ethernet everything works again, but wireless is a no go.

Does anyone have any idea why this might be?


Relevant info:

Firefox says this when I try to access 192.168.15.1:

Failed to Connect          

Firefox can't establish a connection to the server at 192.168.15.1.

Though the site seems valid, the browser was unable to establish a connection.

Using Intrepid 64-bit.

zebariah@Media:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.15.0    *               255.255.255.0   U     0      0        0 eth0
192.168.15.0    *               255.255.255.0   U     2      0        0 wlan0
192.168.122.0   *               255.255.255.0   U     0      0        0 vnet0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.15.1    0.0.0.0         UG    0      0        0 wlan0
default         192.168.15.1    0.0.0.0         UG    100    0        0 eth0

---

### Post by superprash2003 on 2009-03-26
you can but ubuntu would use only one of them for internet access.. it would mostly be eth0 as it chooses the faster one..

---

