---
title: "Help connecting wlan0 to router and eth0 to NAS"
date: 2009-10-22
forum: Networking &amp; Wireless
---

### Post by erffac on 2009-10-22
I'm trying to connect my NAS directly to my computer through the eth0, but I am having trouble.  My connection to my router through wlan0 works fine.

My NAS needs me to give eth0 a static ip address in the 192.168.168.xxx subnet, 225.225.225.0 subnet mask.  I have no idea what values are required in the /etc/network/interfaces for eth0 and what values they need (other than an address and subnet mask).

This is what I have.

auto eth0
iface eth0 inet static
address 192.168.168.100
network ???
netmask 255.255.255.0
broadcast 192.168.168.255
gateway ???

Thanks.

---

### Post by Iowan on 2009-10-22
> **erffac said:**
> My NAS needs me to give eth0 a static ip address in the 192.168.168.xxx subnet, [COLOR="Red"]225.225.225[/COLOR].0 subnet mask. Typo? I presume you meant what you used in your example: netmask 255.255.255.0. You may not need the network and broadcast addresses, but the network would be 192.168.168.0. If there is no other machine on this net, make the gateway the address of the NAS box. 
BTW, unless you have one of the gigabit NIC's that can auto-configure, (or the NAS is capable) you may need a crossover cable to connect the two boxes.

---

### Post by erffac on 2009-10-22
Yes, typo.  The config has the correct netmask value.  The NAS has the ability to connect directly without a crossover cable.


Thanks for your help.  The solution is quite embarrassing--the NAS wasn't connected to eth0.  In my defense, those little fins that connect on the backplate of the motherboard were blocking eth0, so I didn't even realize that there was another connection.

For reference, I got rid of network and broadcast like you suggested and used 192.168.168.1 as the gateway instead of the NAS address, and that did it.


Thanks very much.

---

