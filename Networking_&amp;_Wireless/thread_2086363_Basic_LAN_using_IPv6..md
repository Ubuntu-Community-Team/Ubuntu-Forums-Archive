---
title: "Basic LAN using IPv6."
date: 2012-11-20
forum: Networking &amp; Wireless
---

### Post by sebastian.s on 2012-11-20
I have just started too learn about IPv6 and i must say it is really interesting. 

I have managed to set up a simple Local area network with two hosts, and they are able to communicate using the local-link address. This isn't that difficult since Ubuntu comes with IPv6 pre-configured and all i really had two do was to ping the other machine.

```
ping6 <IPv6-address>%ethx
```Were ethx is the network interfaces from which i send my ping.

But that's link-local, what i want to do next is to set static IPv6 addresses on my hosts. So that i can choose which address they should be using. 

So i edited /etc/network/interfaces in the following way:

```

auto eth0
iface eth0 inet static
pre-up modprobe ipv6
       address <IPv6-address>
       netmask 64

```I have set a static ip on both of the hosts, but to be able to ping each other i have to uncomment this line: **#net.ipv6.conf.all.forwarding=1**
In /etc/sysctl.conf

I'm just wondering, is this the "correct" way  of setting up a IPv6 LAN with static ip's? The part that confuses me is that i must uncomment the line in /etc/sysctl.conf

grateful for all the answers :)

---

### Post by KiLaHuRtZ on 2012-11-20
I do it with sub-interfaces...

```
# The ipv6 network interface
auto eth0:0
iface eth0:0 inet6 static
address <IPv6_Address>
netmask <Mask_Length>
gateway <Router_Address>
```

That's all you need.

---

### Post by sebastian.s on 2012-11-21
> **KiLaHuRtZ said:**
> I do it with sub-interfaces...

```
# The ipv6 network interface
auto eth0:0
iface eth0:0 inet6 static
address <IPv6_Address>
netmask <Mask_Length>
gateway <Router_Address>
```That's all you need.

Aha i see, i will have to try out using virtual ips as well, it can be quite handy :)

---

