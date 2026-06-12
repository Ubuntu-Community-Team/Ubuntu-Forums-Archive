---
title: "Building a LAN"
date: 2009-03-18
forum: Networking &amp; Wireless
---

### Post by muxecoid on 2009-03-18
Hello. I'm new to this so excuse me if the answer is obvious and the question is confusing. There are several computers connected through simple network switch. One of the computers is also connected to external LAN and learns his IP from DHCP server running elsewhere. I want this machine to be able to communicate with other machines on the same switch and identify them yet I do not want any communication between the backend computers in my network and external network. How do I do this? Do I need to install DHCP server somewhere?

Example of what I want it to look like:
machine connected to external LAN is known as mymaster.myorganisation , machines that are connected only through network switch nodeX.mymaster.myorganization and only mymaster.myorganization is seen from othermachine.myorganiztion

---

### Post by bruno9779 on 2009-03-18
Does your switch support VLAN?
If yes you can configure all your needs there and much more (work groups etc)

---

### Post by strife242 on 2009-03-18
There are several ways of setting this up based on what you want to accomplish.

First, the computer connected to the external network will need to NIC's

Lets say eth0 is the external NIC on which you have set up a DHCP client in order for it to receive its settings from the external DHCP.

eth1 is for the internal network, this is connected to the same switch as all the members of your LAN.

You can either set the clients on the LAN up with static IP addresses from the same subnet, in this case make sure you select a private network that is not in the same range as the external network. 

Or if you want the IP addresses to be dynamically assigned you need to install a DHCP server. Either you can get a standalone NAT/PAT ("router") with a built in DHCP server and install it between the external computer and the switch or you can install a DHCP server on the machine listening on eth1.

Then you will have to set up routing between the interfaces in order to pass traffic from the LAN clients to the external network.

---

### Post by muxecoid on 2009-03-18
If I want the machines inside to have statical IP (10.0.0.10-16 for example) do I need to do any extra work except for telling the nodes to use this as IP?

---

### Post by strife242 on 2009-03-18
No, you have to configure each address manually on each client with the same subnetmask and default gateway. You might want to add some DNS servers to your resolv.conf as well.

I suspect you want the computer that communicates with the external network to forward the traffic between the networks so that you can access the outside from your LAN?

If that is the case then you have to set it up as the default GW for the LAN clients and then add routes for it.

---

### Post by muxecoid on 2009-03-18
No, I do not want the frontend computer to work as gateway. The nodes should not see anything outside of their own subnet.

---

### Post by strife242 on 2009-03-18
Then just configure the clients with a private address out of a scope you choose with the corresponding subnetmask.

If you don't add any routes to the "master" then no traffic will be forwarded either.

You can still install a DHCP server if you want the settings to be assigned dynamically if you prefer.

---

