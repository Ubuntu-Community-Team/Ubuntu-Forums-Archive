---
title: "Multiple VPN through NAT"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by eee1000huser on 2009-02-18
Hi,

Can anyone tell me if it's at all possible to have multiple VPN connections NATed through the same NAT box?

I've got a ubuntu 8.10 linux box set up to masquerade from an internal to an external network. Everything works fine so far. I can also use VPN (pptp I think).

The problem is if I try to start a second VPN connection... This one never gets connected. I can only run one VPN connection at the same time.

Both of these VPN connections are to the same VPN server (but using 2 sets of username/passwords).

I've tried to google for answers and came across patch-o-matic. Has anyone successfully installed this on Ubuntu 8.10? Would that help?


Thanks

---

### Post by pvpkiran on 2009-03-25
Hey , Im facing the same problem .
   Pls let me know if u hav found the solution for this


Thank You

---

### Post by sampathz on 2009-03-25
I am the other user in same network as kiran's ;-)


Thank You[/QUOTE]

---

### Post by stas123 on 2009-06-23
Hi, I had the same problem and after some search I found it had something to do with GRE forwarding. I did not look into too much details, but loading the following modules solved the problem:

```

modprobe ip_gre
modprobe ip_nat_pptp
modprobe ip_conntrack_pptp
```I also added these modules at the tail of /etc/modules to have them loaded at boot time.

Hope this helps,

Stas

---

