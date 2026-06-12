---
title: "How can a computer have the same MAC Address with his router?"
date: 2011-08-22
forum: Networking &amp; Wireless
---

### Post by stamatiou on 2011-08-22
Hey guys,
I have read in a forum that a computer can have the same MAC Address with its router in the sane LAN but how is that possible? Isn't every MAC unique? Also I have not understood, when we send a packet to a PC that is not in our LAN the packet should have the IP Address or the MAC Address of the computer that we want to send?

---

### Post by Gwaro on 2011-08-22
The MAC address is burned to the NIC card of each device and therefore unique.
For devices in the same LAN,they use the layer 2 address(MAC) to locate other devices.In the case of a device out of the LAN,an IP address is used,and this is done by the router.

---

### Post by haqking on 2011-08-22
> **stamatiou said:**
> Hey guys,
I have read in a forum that a computer can have the same MAC Address with its router in the sane LAN but how is that possible? Isn't every MAC unique? Also I have not understood, when we send a packet to a PC that is not in our LAN the packet should have the IP Address or the MAC Address of the computer that we want to send?

MAC addresses are unique and they are a 48 bit (12 digit) unique address.

the first half of the address (24 bits) identifies the manufacturer.  The second half or (24 bits) is or should be unique to the device.

There in theory should never be a repeat, however a few years ago mass production of cheap knocks off in China flooded the market with repeat identifiers but it hasnt really been an issue.

The MAC is a hardware (burned) address and the IP is a logical one (dynamic)

IP is routable which is what we need in routed environments usch as the Internet.  Once the packet reaches the LAN associated with the source IP another protocol known as ARP takes over and resolves the IP to the MAC address so it knows where to deliver the packet.

Using software it is also easy to change (spoof) your MAC address to make packets appear to have come from another machine then they really did, this is something you may need to do during WPA cracking for example. However i will not discuss that here ;-)

---

### Post by lmarmisa on 2011-08-22
A MAC address must not be cloned in a LAN or sub-net.

Some routers are able to clone the MAC addresses of other devices. But I believe that this feature is used in other interfaces different than the LAN, for example, the WAN port. 

Imagine that an ISP requires the specific MAC of the user's computer for authenticate the connection. Only one computer could be connected to internet with this configuration. 

But what about if the user wish to extend the connection to internet to more computers?. He has to add a router and this router should  clone the MAC address of the computer that previously was directly connected to internet. The MAC address will be cloned in the WAN port. The router will use a different MAC address not cloned in its LAN port. So there is no conflict with this solution.

---

