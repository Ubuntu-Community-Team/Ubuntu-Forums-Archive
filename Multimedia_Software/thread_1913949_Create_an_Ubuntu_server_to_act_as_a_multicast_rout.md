---
title: "Create an Ubuntu server to act as a multicast router"
date: 2012-01-23
forum: Multimedia Software
---

### Post by TheBigAmbulance on 2012-01-23
I will have the following network setup on the ubuntu server:

eth0:  10.231.102.1/255.255.255.0 - Default Route 10.231.102.254
eth1:  192.168.1.1/255.255.255.0 - PCs

I have a multicast address of 239.224.10.2.  This system will be able to route to it through the default route, so no routing problems.  A PC in the 192 subnet will have a different gateway (I.E. they will not be using the new ubuntu system ip address as a gateway to other networks).  However, I want the new ubuntu systems to be able to respond to an IGMP request so that users can use VLC to view the stream at the 192.168.1.1.

Summary:
- The multicast sources is PIM-Sparse, thereby needing this box to pull the stream in
- The ubuntu box will need to pull the stream and proxy the stream on a reboot
- The ubuntu box will generate a multicast on eth1
- The PCs in the 192 network will use VLC to view the stream at 192.168.1.1 (the ubuntu box would act as a bridge so the 192 network would not be aware of the 239 multicast)

Which would be the best answer:  smcroute or igmpproxy?

I have been using my google-fu to try and find an answer, but there are vary sparse examples online.  My main goal is so that the 192 is oblivious to anything but the 192 network, and doesn't know about anything 'north' of the ubuntu multicast server.

EDIT

smcroute conf file would look something like this I believe:
mgroup from eth0 group 239.224.10.2
mroute from eth0 group 239.224.10.2 source 192.168.1.1 to eth1

---

