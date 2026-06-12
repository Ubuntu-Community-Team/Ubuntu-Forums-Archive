---
title: "Need help setting up interfaces (2 NICs for 2 purposes)"
date: 2009-12-15
forum: Networking &amp; Wireless
---

### Post by Axanon on 2009-12-15
My Ubuntu box has 2 Ethernet NIC cards and I would like to set set them up so 1 is connected to my router (for LAN use only), and the other directly connected to my cable modem. I can stop ingoing/outgoing WAN traffic at my router, but eth1 does not automatically connect.

eth0 is the card I want to connect to the LAN.
eth1 is the card I want to connect to the WAN.

Can somebody please help me set this up?

---

### Post by ubu_can on 2009-12-16
I have (almost) exactly what you want to do:

edit the file /etc/network/interfaces

auto lo
iface lo inet loopback

# The internal (LAN) network interface
auto eth0
iface eth0 inet static
address 192.168.0.191
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1

# The modem-connected network interface
auto eth1
iface eth1 inet static
address 10.168.1.191
netmask 255.255.255.0
network 10.168.1.0
broadcast 10.168.1.255
gateway 10.168.1.1

edit the file /etc/resolv.conf
nameserver 10.168.1.1 (or whatever other nameserver you want)

assumptions: 
-- both interfaces get static address (change it to dhcp, if you so wish)
--your LAN is 192.168.0.xx with your LAN router at 192.168.0.1
-- your modem network is 10.168.1.xxx with your moded address at 10.168.1.1

after you edit them, run
sudo /etc/init.d/networking restart

I hope I did not forget anything... good luck!

---

### Post by Iowan on 2009-12-16
You should be able to leave one connected via Network Manager - especially if it needs to get DHCP address... but */etc/network/interfaces should* work, too.

---

### Post by t0mppa on 2009-12-16
Your LAN NIC (eth0) shouldn't have a gateway configured though, since gateway is by definition the route through which you can connect to other networks, i.e. outside your LAN. Also the main routing table can only have one default route (any gateways configured in the interfaces file will be made into default routes), having more than one will confuse the system and at the worst case render any connections outside your local networks unusable.

---

