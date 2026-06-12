---
title: "What is the use broadcast address?"
date: 2011-02-28
forum: Networking &amp; Wireless
---

### Post by helstreak on 2011-02-28
Reading online, all I get is the broadcast address can be used to send packets of information to all computers on a network simultaneously.  Can that be used during MPI programming or anything of the such?  What is the day to day use of the broadcast address?

Thanks

---

### Post by Hippytaff on 2011-02-28
A broadcast packet will communicate with all machines on a network, so a basic example would be if an administrator wanted to know how many pc's were up, or maybe to do a inventory sweep, though these are just theoretical things, I have no working knowledge of how it is 'actually used' day to day, though for any reason that would require a whole network to be 'addressed'

I'm interested in some of the answers too, now I come to think of it

---

### Post by grahammechanical on 2011-02-28
Here is a quote from linktionary.com

> Applications  that produce broadcast messages include ARP (used by hosts to locate IP  addresses on a network), routing protocols like RIP, and network  applications that "advertise" their services on the network.


Don't know what it means, though.


Regards.

           [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#000000][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#000000]      [/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]

---

### Post by bab1 on 2011-02-28
Network broadcasts are useful for such things as: ```

ARP on IP
DHCP on IP
NetBIOS name location (IP or not)
Routing table updates sent by routers to other routers. 

```

The broadcast domain is the range of the local area network (LAN).

Edit:  
ARP is how an IP address is resolved to a specific NIC (MAC Address)
DHCP Broadcasts is how a host finds the DHCP server
RIP, OSPF, etc. broadcast their routing tables to adjacent routers.
NetBIOS broadcasts COMPUTER Names to all other hosts on the LAN

---

