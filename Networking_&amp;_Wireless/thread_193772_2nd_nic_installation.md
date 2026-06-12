---
title: "2nd nic installation"
date: 2006-06-10
forum: Networking &amp; Wireless
---

### Post by global_dev on 2006-06-10
My server gets ip address from cable modem on eth0 as a dhcp client. To what address do i set the gateway for eth1? Eth0 may change when reassigned a dynamic ip address from the cable co. 

Most dhcp tutorials dont' explain why the broadcast address should be x.x.x.255, and if the ip address of etho changes how it affects the gateway of eth1 and the others or not. i thought the gateway would be the ip address of Eth0. is this correct?

I tried reading some basic networking how-tos and dhcp configuration man pages, but didn't exactly see what i am looking for. I looked at some DHCP and networking maunals in the bookstore and i didn't get a good idea of why i should be assigning for what reason. 

Additionally, I am curious as I turned my router into a switch (no dhcp server), should the switch ever get an address if the wan (uplink) is not used? i have no experience with switches other than those attached to routers and acees points (all-in-one).

---

### Post by Slim Odds on 2006-06-10
[quote=global_dev]My server gets ip address from cable modem on eth0 as a dhcp client. To what address do i set the gateway for eth1? Eth0 may change when reassigned a dynamic ip address from the cable co. 

Most dhcp tutorials dont' explain why the broadcast address should be x.x.x.255, and if the ip address of etho changes how it affects the gateway of eth1 and the others or not. i thought the gateway would be the ip address of Eth0. is this correct?

I tried reading some basic networking how-tos and dhcp configuration man pages, but didn't exactly see what i am looking for. I looked at some DHCP and networking maunals in the bookstore and i didn't get a good idea of why i should be assigning for what reason. 

Additionally, I am curious as I turned my router into a switch (no dhcp server), should the switch ever get an address if the wan (uplink) is not used? i have no experience with switches other than those attached to routers and acees points (all-in-one).[/quote] 
Lots of words there.

Couple of things:
1) with a netmask of 255.255.255.0, the broadcast address is X.X.X.255, it's not a DHCP thing, it's an IP thing

2) if your DHCP server is handing out addresses, the gateway address is usually X.X.X.1

You don't really say what your configuration is, or what you are trying to do.

---

### Post by global_dev on 2006-06-10
[QUOTE=Slim Odds][SIZE="2"]Lots of words there.

Couple of things:
1) with a netmask of 255.255.255.0, the broadcast address is X.X.X.255, it's not a DHCP thing, it's an IP thing

2) if your DHCP server is handing out addresses, the gateway address is usually X.X.X.1

You don't really say what your configuration is, or what you are trying to do.[/SIZE][/QUOTE]

i think my problem is definitions: I have been reading The Linux Documentation Project and lots of howtos and i am trying to wrap myself around what these things are, since i know sometimes things are not what i think they are.

the internal network is 192.168.1.0, 255.255.255.0
ip leases are from 192.168.1.100 to 192.168.1.200
eth1 is 192.168.1.1


per 1) I thought that the DHCP server broadcasts on that IP, to tell you the truth I am trying to figure out what the broadcast actually is... my guess was that clients are listening for that address and the broadcast includes the server's IP of x.x.x.1 to respond to and requests a lease.

per 2) If eth1, which is what the dhcp server is listening on, is 192.168.1.1, is the gateway in the config also 192.168.1.1? Is the gateway to the WAN or LAN, or both? My current thought was there is gateway 192.168.1.1 for the LAN and I imagine in that case i need to connect eth0 and eth1 with a route to allow teh LAN to access the the wan.

I could post configs if i knew which were appropriate to start with, since this involves probably more than one.

thanks.

---

