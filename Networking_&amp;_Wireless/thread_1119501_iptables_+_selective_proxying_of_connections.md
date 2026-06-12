---
title: "iptables + selective proxying of connections"
date: 2009-04-08
forum: Networking &amp; Wireless
---

### Post by shantzg001 on 2009-04-08
Hi

I need some help on iptables (I guess).
I have a gateway G and 3 machines (A, B, C) that connect it to access the internet. I need to selectively route a couple of these machines through proxy server(s) while keeping the 3rd machine's connection untouched. I am guessing that I should be able to find an answer through iptables. Please let me know if someone has done something like this before. 

BTW, the complete end situation would be something like this.
There are 2 proxy servers, 1 running on the gatway itself (192.168.0.1:8080) and another on machine A (192.168.0.2:8080).
Machine A (192.168.0.2) also has a direct/unproxified connection to the internet through the gateway.
Machine B (192.168.0.3)'s traffic is automatically redirected by the gateway through Machine A's proxy server.
Machine C (192.168.0.4)'s traffic is automatically redirected by the gatway through it's own proxy server.

A bit of detail about why I want to do this is that A is my main machine which I use regularly and don't want its connection to be proxified. B has some programs running which I need to test through a custom proxy that I run over machine A. C is an embedded device that constantly accesses some similar data in a certain time range and I'm trying to optimize its net usage
by using squid proxy on the gateway. C is always on even when A is not on so I need its corresponding proxy to be on gateway.
Also, is it possible to do this "on-the-fly", i.e. I don't have to restart any service that leads to breaking of connection.

Thanks

---

### Post by garyalexza on 2009-04-08
To make sure that your connections get directed properly, Machines B & C should use Machine A as their gateway.

Here's what you should put on your gateway (Machine A):

```

iptables -t nat -I POSTROUTING -s 192.168.0.3 -p tcp -m tcp --dport 80,443 -j DNAT --to-destination 192.168.0.2:8080
iptables -t nat -I POSTROUTING -s 192.168.0.4 -p tcp -m tcp --dport 80,443 -j DNAT --to-destination 192.168.0.1:8080

```

That should work as you want... :)

---

### Post by sanemanmad on 2009-04-08
on-the-fly? Yes, just add the iptables rules and your good to go.

As far as what you are trying to accomplish... I am having a hard time understanding. 

GW <-- C
|
A <-- B 

> Machine A (192.168.0.2) also has a direct/unproxified connection to the internet through the gateway. Do you already have an iptables rule that specifies this?

if not, this should work (All you need to do is create a rule that says all traffic (! $B) must go through the gw firewall, then enter another rule forwarding B to A).

```
iptables -t nat -A PREROUTING -i $gateway-interface -p tcp --dport 80 -s ! machine-b -j DNAT --to gateway-ip:8080
```

```
iptables -t nat -A PREROUTING -i $gateway-interface -p tcp --dport 80 -s machine-b -j DNAT --to machine-a:8080
```

---

