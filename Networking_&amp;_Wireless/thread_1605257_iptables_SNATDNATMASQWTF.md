---
title: "iptables SNAT/DNAT/MASQ/WTF?"
date: 2010-10-25
forum: Networking &amp; Wireless
---

### Post by lawl on 2010-10-25
Ok I got a little problem. usually i've come along great with man pages and stuff. but here is a problem that seems a bit to complex for me.
i need a iptables rule, now what i want to do is simply route traffic comming from a specific ip on eth0 to another ip on vpn0.
Here is the actual problem. I have a device in my network, which doesn't support VPN connections. but i need to emulate a LAN for it, actually a LAN connection to one specific ip in the vpn is enough.
Maybe once again to clarify:
the device has 192.168.1.10
my pc's eth0 has 192.168.1.20
my destination is on vpn0 with the ip 10.101.100.30
i CAN NOT modify the standard gateway of the device.

When the device scans the lan and hits 192.168.1.20 my pc should route the traffic to 10.101.100.30 obviously it should also route everything (or at least the response ;-)) from 10.101.100.30 to 192.168.1.10.

on the other side will be the same architecture.

as i said, i've read many papers about iptables, but in the end i was more confused than before, because of this whole SNAT/DNAT/MASQ stuff.

---

### Post by lawl on 2010-10-25
shameless selfbump

---

### Post by Toon Macharis on 2010-11-12
Have you tried adding the following rules?

```
sudo iptables --insert FORWARD --source 192.168.1.10 --destination 192.168.1.20 --jump ACCEPT

sudo iptables --table nat --insert PREROUTING --source 192.168.1.10 --destination 192.168.1.20 --jump DNAT --to-destination 10.101.100.30
```

---

### Post by Toon Macharis on 2010-11-13
I found the following website gives a good explanation about which iptables chains are traversed: [http://www.faqs.org/docs/iptables/traversingoftables.html]("http://www.faqs.org/docs/iptables/traversingoftables.html")

The iptables rule that would forward your network traffic from one IP address to another is:

```
sudo iptables --table nat --insert PREROUTING --source 192.168.1.10 --destination 192.168.1.20 --jump DNAT --to-destination 10.101.100.30
```

You have to make sure that the network traffic is also accepted by the INPUT/FORWARD chains, so if their default policy would be DROP, you explicitly have to add an iptables rule to ACCEPT your network traffic (such as the FORWARD rule in my previous post).

---

