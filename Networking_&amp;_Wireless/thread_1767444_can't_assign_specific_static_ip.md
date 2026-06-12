---
title: "can't assign specific static ip"
date: 2011-05-25
forum: Networking &amp; Wireless
---

### Post by rmjones3 on 2011-05-25
Hello,

Using Ubuntu Server maverick here - after altering /etc/network/interfaces to use a static ip and checking /etc/resolv.conf (no alteration needed) no network services were working at all.  Here are the contents of interfaces:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
    address 192.168.1.100
    netmask 255.255.255.0
    broadcast 192.168.1.0
    gateway 192.168.1.254

```

I was fairly certain that this was verbatim from my previous server which is no longer attached to the network.  After hours of fooling around with no success I changed the address to 192.168.1.99 and it worked perfectly.  So my question is: why?  My old server used 100.  Could the router refuse to give a new server the same address or something like that since that address had been taken in the past?  Just trying to understand the problem.  Thanks.

---

### Post by Iowan on 2011-05-25
Did **ifconfig -a** show the server (interface) with the address? 
If it shows - can you **ping** other machines?
Could you check the router files to see if .100 shows?

---

