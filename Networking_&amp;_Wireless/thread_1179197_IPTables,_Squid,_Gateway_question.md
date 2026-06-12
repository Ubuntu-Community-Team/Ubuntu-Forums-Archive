---
title: "IPTables, Squid, Gateway question"
date: 2009-06-05
forum: Networking &amp; Wireless
---

### Post by ovcrash on 2009-06-05
Hi,

My network is setup like this.

Router (internet)
192.168.0.1

Ubuntu server with two interfaces
eth0 192.168.0.100 (physically connected to router)
eth1 192.168.1.100 (LAN side)

Working Computer
192.168.1.201

So i setup a squid server, in the ubuntu box. And added iptables to redirect port 80 to 3128 so the squid box acts as the proxy and caching server.

But SSL (port 443) doesn't pass the proxy, because of the man-in-the-middle aspect.

**So my question is, how do i redirect SSL from eth1 to eth0 then to the router ?**
I really don't have a clue, i tryed some things but nothing worked.

Thanks for your help!!

---

### Post by ovcrash on 2009-06-09
Anybody has a clue ?

---

### Post by alphacrucis2 on 2009-06-09
> **ovcrash said:**
> Anybody has a clue ?

Squid does support tunnelling of port 443. Of course it can't cache or do anything with the encrypted data but you can use squid acl's to restrict or allow https access to specific sites.


Edit: I think I misunderstood what you are trying to do. Why not configure you browser to use the squid proxy server for http & https and not do the port forwarding at all. That is the standard way to do it.

---

### Post by ovcrash on 2009-06-09
Because i want to use the transparent proxy option.

But i thougth that you could redirect https from eth1 to eth0 then it goes out the gateway ?

kind of like a normal gateway ? But i want to "filter" http in squid.

Is this possible ? using proxy server for http traffic but not for https.

---

### Post by alphacrucis2 on 2009-06-10
> **ovcrash said:**
> Because i want to use the transparent proxy option.

But i thougth that you could redirect https from eth1 to eth0 then it goes out the gateway ?

kind of like a normal gateway ? But i want to "filter" http in squid.

Is this possible ? using proxy server for http traffic but not for https.

What happens it you apply the DNAT only to the http and leave the destination address of the https traffic alone. As long as the squid box is the default gateway for your browsing machine and it allows ip forwarding that should work and take squid out of the picture for https. In other words you just use the squid box as a router for the https traffic. You can still apply destination restrictions using the iptables forward chain on the squid box.

---

### Post by alphacrucis2 on 2009-06-10
> **alphacrucis2 said:**
> What happens it you apply the DNAT only to the http and leave the destination address of the https traffic alone. As long as the squid box is the default gateway for your browsing machine and it allows ip forwarding that should work and take squid out of the picture for https. In other words you just use the squid box as a router for the https traffic. You can still apply destination restrictions using the iptables forward chain on the squid box.

I forgot to say that by default, Ubuntu seems to have ip forwarding disabled so to use your squid box as a router you will need to:

```
sudo sysctl -w net.ipv4.ip_forward=1
```

---

