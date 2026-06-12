---
title: "mDNS across OpenVPN Subnet-Linking Tunnel"
date: 2013-02-22
forum: Networking &amp; Wireless
---

### Post by ChickenLittle on 2013-02-22
Hi all,


I have the following setup:

- Gateway A (10.0/16)
- Gateway B (10.1/16)
- Gateway C (10.2/16)
- Misc. Clients (10.4/16)

Gateway B and C have an openVPN tunnel to Gateway A. Other clients (such as iOS devices and computer) can also connect to Gateway A through a [different] tunnel. Each gateway is set to route traffic destined for each of the other subnets across the tunnel.

So, a traceroute to a client from a 10.0/16 device would be:

- Gateway A
- Destination Device

And a traceroute to a 10.1/16 device from a 10.0/16 device would be:

- Gateway A
- Gateway B
- Destination Device


What I want to do is have mDNS repeated from each subnet to each other subnet.

So:

A broadcast from 10.0/16 should go to 10.1/16, 10.2/16 and 10.4/16.
A broadcast from 10.1/16 should go to 10.0/16, 10.2/16 and 10.4/16.
A broadcast from 10.2/16 should go to 10.1/16, 10.0/16 and 10.4/16.
A broadcast from 10.4/16.... well, read below.

I know that I need to have a daemon running on one device on each subnet for this to work (and therefore I can't really repeat the mDNS broadcasts from 10.4/16 since that's not a physical subnet, and that's OK).

However, I need one that will repeat from one subnet to the others and not vice versa so I don't get ping-pong effects (i.e. 10.0/16 being repeated to 10.1/16 and then that subnet's repeater sending it right back to 10.0/16)

I would appreciate any suggestions - including suggestions for a better forum to which to post!



Currently, only one Gateway is set up, and it's running Linux Mint (which is similar enough to Ubuntu to have this forum be of some help)

The others will either be other Linux Mint computers or DD-WRT routers.


Thanks!

---

