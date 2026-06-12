---
title: "Vlan - nat"
date: 2010-02-28
forum: Networking &amp; Wireless
---

### Post by ICEB3AR on 2010-02-28
Hi there,

I basically want to build a gateway for different vlans. I got a 802.1q tagged VLAN from my switch about a port and define the vlans in my interface after installing the package ("vlan")

e.g.
```
auto eth0.99
iface eth0.99 inet static
address 192.168.99.1
netmask 255.255.255.0
```

Can i now easily define a NAT rule like for eth0 only for eth0.99 ? is the vlan tag then out of the tcp/ip package ?

Sorry, but i can not test this. If I build this it had to go immediately in production. 

If this did not work. How would i define a gateway for vlans ?

Have a nice evening.

---

### Post by ICEB3AR on 2010-03-03
Bump

---

### Post by coutts99 on 2010-03-03
> **ICEB3AR said:**
> Can i now easily define a NAT rule like for eth0 only for eth0.99 ? is the vlan tag then out of the tcp/ip package ?

Yes and yes, I have done this in the past

---

### Post by ICEB3AR on 2010-03-03
Thank you very much for your answer coutts99. 
=)

---

