---
title: "OpenVPN help required"
date: 2009-10-01
forum: Networking &amp; Wireless
---

### Post by Strange_Movement on 2009-10-01
I have a server that is also acting as a router for the rest of my network and I would like to be able to use *OpenVPN* to connect machines elsewhere on the planet to my internal network. I would also like the ability to decide whether to route internet traffic through my internal network for the external clients in case they are connecting from an untrusted wireless hot spot. I don't really have the first idea of how to do this so a howto matching my requirements would be really appreciated. I assume it would help if I gave some details about my current network configuration, so here they are:

**eth0** is connected directly to a Virgin cable modem and has my external IP assigned to it

**eth1** is connected to my internal network and is statically assigned 192.168.0.250
**eth1** also has DHCP running on it to assign IP addresses to the client machines

obviously I also have a firewall using *iptables* so I need to know what ports to open

Any help would be greatly appreciated and any further details of my current set up will be supplied if required.

Thanks in advance !

---

### Post by mattkoehn on 2009-10-01
Skimmed your post but here is the idea. There is an option in the server config for openvpn that decides if your clients see each other or other devices on the network.

If you wanted some clients to be able to see your network, and others not to, you would have to have two openvpn server configs running. 

This would have to be on two different network interfaces.

However, they can be virtual interfaces which there is plenty of info on the interweb on creating. So just create a new config that allows your clients to see your network, put that on a new virtual interface, and have anyone you trust to see your network connect to that virutal ip as opposed to the 'insecure' server config and virutal ip(or actual ip). 

Natually you can have different keys or each client or for each port. Ideally each clients though.

---

### Post by Strange_Movement on 2009-10-02
Thanks for the reply. Unfortunately I'm not really that good at the practicalities of the actual "how to". I understand the concepts but I need more help with finding a step by step set of instructions that I can tailor to my requirements. Any further pointers to relevant articles would be helpful.

---

