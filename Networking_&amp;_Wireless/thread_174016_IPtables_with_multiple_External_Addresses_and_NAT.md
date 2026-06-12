---
title: "IPtables with multiple External Addresses and NAT"
date: 2006-05-11
forum: Networking &amp; Wireless
---

### Post by Tnarg on 2006-05-11
Hi,

I have a computer that I would like to use as a router. This computer will be used to create a private network within a private network. I have around 10 static IP addresses reserved on the external private network with up to 50 computers running on the internal private network. Until now every computer has been connected to the main network with only the IP addresses different and a computer that did some basic NAT and DNS serving. Problem being that people have learn't to use the internal private network to get unrestricted Internet access. Therefore the internal network needs to be physically isolated from the rest of the building. 

Only 1 of these addresses has unrestricted Internet access which is required by all the machines on the internal network. At times some machines on the internal network must be available on the external network at one of the other static addresses. I also need to filter out any traffic from the rest of the network that doesn't match any of these addresses due to large amounts of network traffic. 

So far I believe the best way to allow external access to some computers is to alias the IP addresses to the Internet interface of the router and forward the connections to the machines internally that are using an internal network IP address. This is not the preferred option though. My preferred option would be to allow unrestricted access for these IP addresses on the internal private network and filter out all traffic not required for these machines but I'm not sure if this is possible or not. If anyone can point me in the right direction that would be great.

I have installed Ubuntu with Firestarter but I also have some experience with using IP tables from the command line as that is how the current solution was configured. Network interfaces are also not much of an issue as I can install around 10 if required (but I don't think that this is necessary).

More specific information:

External private IP address range: 10.30.0.0
Internal private IP address range: 192.168.17.0

Reserved IP addresses: 10.30.0.190 - Unrestricted
Other Reserved addresses: 10.30.0.110, 10.30.0.187

This entire network is then secured as much as possible from the big bad world so security is not really a concern. If any more information is required just shout.

Thanks again for any help.

---

### Post by mips on 2006-05-11
I tried to read this but my head started spinning so i gave up. Hard to distinguish between the different networks.

It might be a better idea to refer to networks A, B & C or Red & Blue etc. Currently they just sound the same and then you refer to a main network & where does the internet connect to ? A simple diagram would also make a lot more sense.

I suppose if I sat down and read it over while drawing and translating i would get it but unfortunately i don't have the time.

---

### Post by bishop1641 on 2007-02-23
I am curious, if your experienced with iptables have you considered using iptables directly and managing it through the webmin interface. Between your packet filter section, mangle, and nat area you should be able to build what you need.

---

