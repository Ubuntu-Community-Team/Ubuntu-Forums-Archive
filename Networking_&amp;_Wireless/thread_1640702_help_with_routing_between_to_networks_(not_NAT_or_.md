---
title: "help with routing between to networks (not NAT or Internet)"
date: 2010-12-08
forum: Networking &amp; Wireless
---

### Post by WelshPanther on 2010-12-08
Hi People,

I am a noob at Linux and need some help with a project.

I have two network (192.168.0.xx and 192.168.1.xx). Neither connect to the internet and will never connect to the internet.

I with to setup a linux box to act as a gateway between the two networks. i.e device at 192.168.0.1 sends data to 192.168.1.2 and so on.

All the examples of iptables have been for internet gateways with NAT.

My ultimate goal is to use netem to slow down the packets to simulate a satellite link, then see how slow I can get before breaking the protocol in use (industrial).

Some help would be appreciated as timescales are short.

So far I have installed Ubuntu 10.10, have two networks cards (one on each network) and have enabled ip-forwarding.

Thanks

Patrick

---

### Post by sedawk on 2010-12-08
Hello!

I always thought that enabling IP forwarding is all you
have to do to make it work!

I assume your Linux box has the IPs
192.168.0.1 and 192.168.1.2

Let's assume you have a PC at 192.168.0.7
If this PC has to send packets to 192.168.1.x he needs
to know that 192.168.0.1 is the gateway for 192.168.1.x
(only for that network or a default gateway for all traffic
 with a target in the non-local subnet).

If the PC 192.168.0.7 wants to send a packet to 192.168.1.99
he sends it to 192.168.0.1 and because IP forwarding is
enabled the linux box will forward the packet into the
192.168.1.x network.

If you think iptables gives you trouble you can try to
turn it off temporarily.

You can also try to run "tcpdump -i any" to see all
network traffic.
E.g. to monitor any traffic for PC 192.168.0.7 you would
do a "tcpdump -i any host 192.168.0.7"

---

### Post by WelshPanther on 2010-12-08
Okay, well there's a misunderstanding here.

My device is on 192.168.0.1
My linux box has eth0 on 192.168.0.80
and the other is eth1 on 192.168.1.80
my other device is on 192.168.1.2

both devices (not PC's) have been configured to a router at 192.168.x.80 respectively

I want to get ping and other stuff working between 192.168.0.1 and 192.168.1.2.

I have flushed the iptables in case they were interfering.

> **sedawk said:**
> Hello!

I always thought that enabling IP forwarding is all you
have to do to make it work!

I assume your Linux box has the IPs
192.168.0.1 and 192.168.1.2

Let's assume you have a PC at 192.168.0.7
If this PC has to send packets to 192.168.1.x he needs
to know that 192.168.0.1 is the gateway for 192.168.1.x
(only for that network or a default gateway for all traffic
 with a target in the non-local subnet).

If the PC 192.168.0.7 wants to send a packet to 192.168.1.99
he sends it to 192.168.0.1 and because IP forwarding is
enabled the linux box will forward the packet into the
192.168.1.x network.

If you think iptables gives you trouble you can try to
turn it off temporarily.

You can also try to run "tcpdump -i any" to see all
network traffic.
E.g. to monitor any traffic for PC 192.168.0.7 you would
do a "tcpdump -i any host 192.168.0.7"

---

### Post by WelshPanther on 2010-12-08
Ahhh HAH

Okay, I have re-installed Ubuntu.

Added IP-Forward and hey presto it works.

I think firestarter had done something nasty somewhere I didn't know about when I was trying various software packages.

Now to play with tc to slow the packets down.

Thanks

---

