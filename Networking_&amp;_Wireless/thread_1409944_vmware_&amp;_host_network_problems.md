---
title: "vmware &amp; host network problems"
date: 2010-02-18
forum: Networking &amp; Wireless
---

### Post by Mrekko on 2010-02-18
Hello guys,

I have a little problem. I have installed a ubuntu server 9.04 im vmware and windows vista as host. 

I want to connect to ubuntu from my host with **putty**. 

My vista network configurations are the follow:

Ip: 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.1

Ubuntu network confgurations:

Ip: 192.168.1.50
netmask 255.255.255.0
gateway 192.168.1.1

Im using nat in the vmware. 

The problem is that i can´t connect to ubuntu via SSH. I already installed ssh server and ssh client in the ubuntu machine.

I can´t ping each one either! 

Im stuck on this guys... what is the problem!?

Thanks!

---

### Post by DGortze380 on 2010-02-18
> **Mrekko said:**
> Hello guys,

I have a little problem. I have installed a ubuntu server 9.04 im vmware and windows vista as host. 

I want to connect to ubuntu from my host with **putty**. 

My vista network configurations are the follow:

Ip: 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.1

Ubuntu network confgurations:

Ip: 192.168.1.50
netmask 255.255.255.0
gateway 192.168.1.1

Im using nat in the vmware. 

The problem is that i can´t connect to ubuntu via SSH. I already installed ssh server and ssh client in the ubuntu machine.

I can´t ping each one either! 

Im stuck on this guys... what is the problem!?

Thanks!

You want a Bridged Adapter, or Host-Only. Not NAT.

---

### Post by Mrekko on 2010-02-20
Yes that worked!

Thank you.

:)

---

