---
title: "configuring tw0 IP adresses"
date: 2009-03-24
forum: Networking &amp; Wireless
---

### Post by mairot on 2009-03-24
Hi all,

  i'm having those 2 IPs

172.21.142.111

and 172.21.242.100.

I want to configure them but does not work. 

I have tried eth0 and eth0:1, eth0 and eth1 but was never able to have both working at the same time.

auto eth0
iface eth0 inet static
        address 172.21.142.111
        netmask 255.255.255.0
        network 172.21.142.0
        broadcast 172.21.142.255
        gateway 172.21.142.3
        dns-nameservers 1.2.3.4
        dns-search this.is.mydsn server.com

## The backup network interface
auto eth1
iface eth1 inet static
       address 172.21.242.100
       netmask 255.255.255.0
       network 172.21.242.0
       broadcast 172.21.242.255
       gateway 172.21.242.3

This servers is connected to a CISCO switch.

---

### Post by blackgr on 2009-03-24
first of all... are these ips from these same isp? or you use something like 2 ethernets with 2 routers?

---

### Post by mairot on 2009-03-24
This server is at work. Not directly connected to the internet, and not used to surf on the internet.

---

### Post by blackgr on 2009-03-24
please show e the output of 

```
ifconfig -a
```

cause i dont really get a clear picture of the problem

---

### Post by BkkBonanza on 2009-03-24
Your two ips need to be on the same subnet. You have 172.21.142.111 and 172.21.242.100.
Your subnet mask is 255.255.255.0 but if you want to use those ips together on the same network then your subnet mask needs to be 255.255.0.0

Using eth0 and eth0:1 is the correct way. For exact syntax just google for a tutorial on multiple ips on same nic. Like this one eg.

[http://linuxhelp.blogspot.com/2005/05/setting-up-multiple-ip-addresses-on.html](http://linuxhelp.blogspot.com/2005/05/setting-up-multiple-ip-addresses-on.html)

There's heap out there. Use google - it's faster.

BTW your question is confusing too - is this one netowrk card or two and one server or two and one network or two, and one gateway or two?

---

