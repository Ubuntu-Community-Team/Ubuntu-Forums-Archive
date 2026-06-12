---
title: "Ubuntu box with two network cards (one for LAN, one for XP box)"
date: 2009-03-13
forum: Networking &amp; Wireless
---

### Post by mbrennwa on 2009-03-13
Dear All

I am trying to use an Ubuntu box to sit in between a company network (with Internet access) and a Windows XP machine. If possible, the XP box should only see the Ubuntu box (and it's shares), but the company network and the internet (I wan't to keep it out of reach from Viruses and the IT people in our institute).

The Ubuntu box has two ethernet cards installed. One card is connected to the company network, the other is connected to the XP box using only a cable with nothing in between. The connection between the Ubuntu box and the company network works flawlessly, but the connection between the Ubuntu box and the XP box does not (there is no sign of a connection on both machines). I am almost sure my network settings are not well.

Here's my /etc/network/interfaces on the Ubuntu box:

--------
auto lo
iface lo inet loopback

iface eth0 inet dhcp
auto eth0

iface eth1 inet static
address 192.168.0.1
netmask 255.255.255.0
auto eth1
--------

I can't say much about the network setup on the XP box. I poked around in the Networking Control Panels, but I couldn't establish a connection (I am absolute newbie on Windows, though).

I searched the forums, but I couldn't find much help on this. However, I was not sure what keywords to use in my search. Any help and suggestions are greatly appreciated!

Thanks
Matthias

---

