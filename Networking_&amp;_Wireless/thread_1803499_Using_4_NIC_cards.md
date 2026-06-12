---
title: "Using 4 NIC cards"
date: 2011-07-13
forum: Networking &amp; Wireless
---

### Post by ajpeters on 2011-07-13
I am setting up a class using a vmWare ESX server.  Because of security proceedures, the students are not allowed to connect directly to the internet.  Because of file space, the are severated on 3 servers.  I am trying to set up a server that connects to the internet and all 3 subnets that the students are on.

I have configure 4 virtual NICs 1 with DHCP connected to the internet.  The other 3 goes to each student network.  I can get 2 working at a time.  1 using the DHCP and 1 of the other networks.  It seems to be order dependent.  On the main server I can ping the local address.  When I ping the students systems, I can reach 1 but not the other 2.  I get a host unreachable message.

Is there a limitation to 2 NICS.  If not, is there any magic incantation to run the 4 nics?

---

### Post by idlemind324 on 2011-07-13
A couple questions:

You are using ESX so how do you have your virtual switch(es) configured?

How are devices on the "router" server setup, are they virtual nic's at inside the VM or are the virtual nic's created in ESX and the "router" server sees them as a physical nic?

If the virtual nic's were configured in ESX then we need to make sure that they are assigned to the right vswitch to be able to talk to the other servers.

Continuing that assumption you then need to make sure that the "router" box has each interface configured properly. By that I mean have each nic assigned an address to that particular subnet and automatically you should have a route (verify it) that connects you the "router" box to each of those subnets. You should then be able to ping each network both ways (assuming you don't have a firewall running yet that might be blocking traffic).

Once you have the basics of communication handled you can then setup IP tools to masquerade traffic to from each interface. I actually haven't done that part but I don't see any reason why that wouldn't work. Once open communication is up then I would worry about locking down ports and communications between the networks.

---

### Post by ajpeters on 2011-07-13
I have forwarded this response to the network specialist in charge of the network.  It appears I can "talk" to the internet and one other network, and can assign one of the virtual networks at a time.  Does this make a difference in your questions?

---

### Post by idlemind324 on 2011-07-14
Have a look at my two attachments. If you're still up to tackling this I would like to see screen shots like the two I posted from  your environment. The VM properties I'd be interested in seeing is the router (server). You may have more vswitch's than I posted as this is just a test network that I posted the screen shots from.

---

### Post by ajpeters on 2011-07-14
I do not think I have permission to do a print screen of the 1st item.  The second I will get to Friday AM.

---

