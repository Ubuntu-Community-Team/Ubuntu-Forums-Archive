---
title: "Static and DHCP addresses"
date: 2010-01-23
forum: Networking &amp; Wireless
---

### Post by illwrath on 2010-01-23
Is it possible for me to configure my laptop so it will use a fixed IP if I'm on my home network but will use DHCP if I'm out somewhere else?  I have seen commands to switch my wireless card to static but none that could let my wireless choose.

---

### Post by sp0nge on 2010-01-23
sort of...

The Network Manager has a GUI for switching from static to dynamic IP, but I prefer to do this by editing the /etc/network/interfaces file as follows:

#For Static IP
auto eth0
iface eth0 inet static
address 192.168.1.3
network 192.168.1.0
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1

#For DHCP
auto eth0
iface eth0 inet dhcp

Then, simply comment out which lines you DONT want to use to activate the proper choice for the network. Be sure to only have one in effect at a time.

---

### Post by darkod on 2010-01-23
> **illwrath said:**
> Is it possible for me to configure my laptop so it will use a fixed IP if I'm on my home network but will use DHCP if I'm out somewhere else?  I have seen commands to switch my wireless card to static but none that could let my wireless choose.

It seems you need static IP for home and you might be able to achieve this another way. If you are using a router to distribute your home internet, open the router configuration and look for DHCP Clients list. On most routers there will be check box on the side to allocate the same IP to that client all the time (it knows clients by MAC address).
That way you can keep settings on DHCP but in a way have a static IP at home, it will always be the same. So you can set up port forwarding or what ever you need the static IP for.

---

### Post by Iowan on 2010-01-23
+1 I'm also fond of using the DHCP server to issue a static lease based on MAC address. Then (as mentioned) the machine can stay configured for DHCP.

---

### Post by darkod on 2010-01-23
Plus, I forgot to mention, it's OS independent. Regardless whether I boot into ubuntu or windows, my desktop has the same IP.

---

