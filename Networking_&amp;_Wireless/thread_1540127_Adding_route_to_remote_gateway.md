---
title: "Adding route to remote gateway"
date: 2010-07-27
forum: Networking &amp; Wireless
---

### Post by debruin on 2010-07-27
I am running 10.04 and am trying to add a route to a remote network using a gateway that is NOT on the local subnet. I am not messing with the default GW as all the other posts I can find are.

I am using public IP addresses, but all of this is contained behind a firewall.  I need to add a route to a private network (192.168.1.x) that is behind a router attached to a different subnet. 

The current routing table looks like this:

```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
xxx.xxx.108.48  0.0.0.0         255.255.255.240 U     1      0        0 eth0
0.0.0.0         xxx.xxx.108.49  0.0.0.0         UG    0      0        0 eth0

```The remote network is 192.168.1.0/24 and it is reachable via xxx.xxx.37.203. I can ping the gateway no problem.  However when I try to add a route to this network I get an error.

route add -net 192.168.1.0 netmask 255.255.255.0 gw xxx.xxx.37.203
SIOCADDRT: No such process

I assume this is because the GW is not on the local subnet.  When I try this on a machine that is connected to the xxx.xxx.37 network, everything works fine and I can reach the remote network.

I even tried adding a static route to the gateway, but that did not help.
route add -host xxx.xxx.37.203 gw xxx.xxx.108.49

Is there a way to do this or am I out of luck?

Thanks.

---

### Post by YesWeCan on 2010-07-27
As I understand things the whole purpose of subnets it to stop a NIC being able to talk to devices on a different subnet. So I don't think you'll get very far trying to route to gateway x.x.37.203 using eth0 on x.x.108.48/28.

Instead, you may need another NIC, eth1, that has an ip on the x.x.37.203 subnet. Then you route traffic destined to 192.168.1.0/24 to gateway x.x.37.203 via eth1. Something like 'sudo route add -net 192.168.1.0/24 gw x.x.37.203 dev eth1'

---

