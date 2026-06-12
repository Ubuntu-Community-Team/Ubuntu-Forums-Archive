---
title: "configuring multiple NICs"
date: 2009-07-11
forum: Networking &amp; Wireless
---

### Post by boondocks on 2009-07-11
If the system has 2 NICs, and each card is on a different network then
is it possible to do this in the "/etc/network/interfaces" 

auto eth0
iface eth0 inet static
address 192.168.11.9
netmask 255.255.255.0
gateway 192.168.11.1

auto eth1
iface eth1 inet static
address 192.168.33.15
netmask 255.255.255.0
gateway 192.168.33.1

---

### Post by jonobr on 2009-07-11
If your asking from a networking addressing point of view,
yes, these are two separate route-able networks and they will be treated as such.

However, If your asking if thats all you need to do, then post check your ifconfig shows the right config for your cards, and you should enable ipforwarding on the server as well so it knows its a router.
You can check if IPv4 forwarding is enabled by using 

```
sysctl net.ipv4.ip_forward

```

---

### Post by boondocks on 2009-07-11
> **jonobr said:**
> If your asking from a networking addressing point of view,
yes, these are two separate route-able networks and they will be treated as such.


Yes, but please correct me...

This is what I need:
[LIST]
[*]Two NICs configured on this system.
[*]Each NIC will be on a different subnet.  192.168.11.*   and  192.168.33.*
[*]From this system, I should be able to scp and ssh any host on 192.168.11.*   and  192.168.33.*
[*]Any host on 192.168.11.*   and  192.168.33.*  should be able to scp and ssh my system.
[*]Router 192.168.11.1 has its own unique WAN ip address X
[*]Router 192.168.33.1 has its own unique WAN ip address Y
[*]Router 192.168.11.1 allows some external hosts to scp and ssh my system.
[*]Router 192.168.33.1 allows some external hosts to scp and ssh my system.
[/LIST]

With the above configuration, will all this be possible.

---

### Post by jonobr on 2009-07-12
I would need to see a network diagram of what your trying to do and how the network would be setup, how client devices view the network, 
i.e. what is the default route and so on.

If you could provide a diagram it may help understand the network setup a bit more.

---

### Post by Iowan on 2009-07-12
Seems like it *should* work.  The **route** (gateway(s)) may need some tweaking.

---

### Post by boondocks on 2009-07-12
> **Iowan said:**
> Seems like it *should* work.  The **route** (gateway(s)) may need some tweaking.

So with regards to routing, is there an order of precedence?
Since we have
gateway 192.168.11.1
and
gateway 192.168.33.1

If I want to ssh into 192.168.33.7
what happens?

---

### Post by superprash2003 on 2009-07-12
take a look at this [http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/](http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/)

---

