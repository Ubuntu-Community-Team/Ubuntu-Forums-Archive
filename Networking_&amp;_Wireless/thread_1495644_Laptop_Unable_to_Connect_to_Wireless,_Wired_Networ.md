---
title: "Laptop Unable to Connect to Wireless, Wired Networks"
date: 2010-05-28
forum: Networking &amp; Wireless
---

### Post by Jaded Misanthrope on 2010-05-28
I'm trying to install Ubuntu 10.04 on my Toshiba A200-12U laptop (with an Atheros AR5007EG wireless card), but networking is being problematic.

I entered Network Configurations and tried to get 'Auto eth0' working -- I went to Edit > IPv4 settings and filled in 'Addresses' with the details of my connection:
Address: 192.168.1.254 (the local IP of my router)
Netmask: 255.255.252.0
Gateway: 94.195.208.1
DNS servers: 87.194.255.154, 87.194.255.155

I filled in the routes section with the same information, but left the section for Metric blank. This has the network report as connected, but I have no Internet access.

Wireless doesn't work either: trying to connect to my own home network fails even with the correct password, as does trying to connect to an unsecured network.

---

### Post by Jaded Misanthrope on 2010-05-28
I'm sorry to bump this, but this is quite an urgent matter -- if at all possible, I need to find out how to fix this before tomorrow morning.

---

### Post by Iowan on 2010-05-28
Maybe I'm missing something, but it looks like your gateway will be inaccessible - it should be in the same subnet. The gateway will probably be the address of your router - the machine's address must be something other than that of the router... but should be in the same subnet. If the router is also a DHCP server, you should avoid addresses in the DHCP range.

---

### Post by Jaded Misanthrope on 2010-05-28
I changed the address to 192.168.1.66 and the gateway to 192.168.1.254 -- but I still can't connect to the Internet via Ethernet. Have I misinterpreted you?

---

### Post by Iowan on 2010-05-28
Can you ping the router (from a terminal)?
Can you ping internet by IP address (74.125.95.103)?

---

