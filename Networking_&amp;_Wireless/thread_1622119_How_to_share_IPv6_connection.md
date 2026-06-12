---
title: "How to share IPv6 connection"
date: 2010-11-15
forum: Networking &amp; Wireless
---

### Post by canonized on 2010-11-15
Hello,

I have a small wireless network running IPv6 connected though a 802.15.4 usb stick, and a network connection through eth1. I can access the nodes on the wireless network from my computer, but not from any other on the wired LAN. Also the nodes on the wireless cannot see even the address of eth1. I'm guessing i have to forward all packets from the wireless to eth1 in some way, but am unable to find an guides for this with IPv6.

Any help much appreciated

---

### Post by p1mrx on 2010-11-16
That's an interesting question.  Could you describe more about your network?  Is that ZigBee, or 6loWPAN, or what?

Could you give an example of an IPv6 address from one of your devices?  I'm wondering which part of the address space they're allocated from.  I'm assuming just link-local (starts with fe80:: )?

Do the devices also have IPv4 addresses, or are they IPv6-only?

Does your Ubuntu machine currently have an IPv6 connection?  If so, from which ISP / tunnel broker?  Can you reach [http://ipv6.google.com/](http://ipv6.google.com/) ?

One thing you'll need to do is enable IPv6 forwarding:
$ sudo sysctl -w net.ipv6.conf.all.forwarding=1

You'll also need to assign proper addresses and routes, so the packets know where to go in each direction.  The radvd daemon will advertise an address range and a default route into the network, but you'll need to know which address range to use before setting that up.

You'll either use an ISP-delegated range, 6to4, or (if the devices don't need to talk to the Internet) a unique local address (ULA) range.  But, which of those to use depends on your situation.

---

### Post by canonized on 2010-11-16
Hello there, thanks for the reply.

The wireless network is 6LoWPAN, nodes are running Contiki. The nodes actually have global addresses, for example aaaa::11:22ff:fe33:44.

All devices are IPv6 only. My machine does not have a IPv6 connection now with a broker. But i dont think its required right now, although might get it later on. Now i just want IPv6 connectivity from computers on the ethernet to the wireless.

The edgerouter(usbstick) has these address: aaaa::12:13ff:fe14:1516, fe80::12:13ff:fe14:1516

eth1 has: aaaa::20f:feff:fe3c:4ca3, fe80::20f:feff:fe3c:4ca3


I have set up radvd with the aaaa prefix, and set ipv6 forwarding and its working. The use case is this: All the nodes report via REST to a webserver on the ethernet(maybe later on the internet), and the server should be able to poll the nodes. Now if I set my webserver to listen on the edgerouter interface(aaaa::12:13ff:fe14:1516) the nodes can see and connect to it. But outside computers can still not see the nodes or the server.

So what i need is have all packets from wireless routed out on eth1 and vice versa. This way i should be able to set my webserver to listen on eth1, and have it accessible by everyone.

---

### Post by p1mrx on 2010-11-16
Ok, so the key point is, for routing to work, each network segment needs to have a unique /64 prefix.  If all the 6lowpan devices (including the USB stick on your Ubuntu machine) use aaaa::/64, then you'll need a *different* prefix (for example, aaab::/64) for your eth1 interface, and all devices connected to the same switch.

The prefixes need to be different so that the devices know when an address is off-link, and needs to be reached via a router instead.

Also, other servers on your eth1 network will need a route to the 6lowpan network using eth1 the ubuntu machine as a router:
$ ip -6 route add aaaa::/64 via aaab::20f:feff:fe3c:4ca3

(And, for the sake of correctness, you should be using /64s out of a fdXX:XXXX:XXXX::/48 block, where the X's are random.  That's a unique local address:
[http://en.wikipedia.org/wiki/Unique_local_address](http://en.wikipedia.org/wiki/Unique_local_address) )

---

### Post by canonized on 2010-11-18
I tried your solution but am getting: RTNETLINK answers: Invalid argument

I also tried sudo ip -6 route add aaaa::/64 dev usb0 via aaab::20f:feff:fe3c:4ca3. But that resulted in RTNETLINK answers: No route to host.

---

### Post by p1mrx on 2010-11-18
The people in #ipv6 on Freenode may be able to help you work out the details.

---

### Post by sanderj on 2010-11-22
@canonized:

What is your setup? Is it this:


 LAN 0 (wireless) --- eth0-MAINsystem--eth1--- LAN 1 (other devices)

If so:
[LIST]
[*]is the MAINsystem also the default (IPv6) gateway to Internet? (Hopefully it is: it makes things easier)
[*]can devices on LAN0 reach the MAINsystem, and the other way round?
[*]can devices on LAN1 reach the MAINsystem, and the other way round?
[*]what are the IPv6 subnets used on LAN0 resp LAN1?
[*]do you use the public IPv6 addresses to try to reach the other LAN? (It won't work with the fe80 addresses)
[/LIST]

---

### Post by canonized on 2010-11-25
Hello there,

I found a fix, simply adding the aaaa::1 to usb0 did the trick. Thanks for your time and interest.

---

