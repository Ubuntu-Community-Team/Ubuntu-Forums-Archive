---
title: "IPv4 and Ipv6 rouitng"
date: 2013-05-22
forum: Networking &amp; Wireless
---

### Post by hrisikeshsahu on 2013-05-22
Hi All,
I have a ubuntu desktop with two interface cards and  both the interface are in two different subnet.
I want to enable IPv4 and Ipv6 routing on this .

Regards

---

### Post by Drenriza on 2013-05-22
Why do you want a single desktop / server to have a IPv4 and a IPv6 address on two different NIC's?
What is the goal?

The only reason i see their would be a "need" for this is if you work at a firm where you have resources in two different networks.
And one use IPv4 and the other IPv6, which is given out by two different DHCP servers.

Even tho i have never experienced a firm doing so, because it does not make much sense.

---

### Post by The Cog on 2013-05-22
You can enable IP forwarding by editing /etc/sysctl.conf. The two lines you need to uncomment (remove the leading #) are:
```
net.ipv4.ip_forward=1
net.ipv6.conf.all.forwarding=1
``` and rebooting.

But this is only a small part of your problem. You need to (somehow) get all the other devices in the network to use your PC as the gateway between the two networks. 

You could configuring the existing routers to know which other networks should be reached by sending packets to your PC, by configuring static routes in them.

Or you could configure the DHCP servers to tell other PCs to use yours as their default gateway.

Or you could configure your PC to advertise routes to the existing routers, which will involve knowing what routing protocols the existing routers are using, and perhaps the encryption keys they use in those protocols.

---

### Post by Drenriza on 2013-05-22
> **The Cog said:**
> You can enable IP forwarding by editing /etc/sysctl.conf. The two lines you need to uncomment (remove the leading #) are:
```
net.ipv4.ip_forward=1
net.ipv6.conf.all.forwarding=1
``` and rebooting.

But this is only a small part of your problem. You need to (somehow) get all the other devices in the network to use your PC as the gateway between the two networks. 

You could configuring the existing routers to know which other networks should be reached by sending packets to your PC, by configuring static routes in them.


You get it to sound like, that he want to use the desktop as a gateway between the two networks. _Which makes 0 sense_. Besdies that,
you don't need to advertise information from the PC, the routers already know what routes they are directly connected two, which in two end points should be a /30 address.
This address should then be advertised by the router and not the pc ^.- Only IF you got more then 1 router in the network, else it's pointless since LAN communication is layer 2 communication and not layer 3.

So you only need a route back from the PC to the network.

> **The Cog said:**
> 
Or you could configure the DHCP servers to tell other PCs to use yours as their default gateway. 

Are we starting man in the middle listening?

Again, i'am wondering what the end goal is ,)

---

### Post by hrisikeshsahu on 2013-05-22
Hi All,
Nice to your reply.
I am looking for a IPv6 certification for our device which has Ipv6 host stack. and i want to use Ubuntu as one of the vendor for IPv6 interoperability test. 
For this I want to make Ubuntu as IPv6 router. IPv4 is not required one. 

I understand the sysctl for IPv6 forwarding.

We will have small network. there will a Ubuntu router with two interface card and each interface will be connected two different  Ipv6 hosts.
My question is  -
> How to enable IPv6 on Ubuntu?
> How to enable gateway for IPv6 in Ubuntu?
> Router may require to do send Neighbor advertisement for Host Neighbor solicitation . 

The end goal is to make Ubuntu desktop as Ipv6 router.

Regards

---

### Post by The Cog on 2013-05-22
> How to enable IPv6 on Ubuntu?
IPv6 is enabled in Ubuntu. Nothing to do except configure the addresses on the interfaces. For a router, this would be something you do manually. e.g.
```
sudo ifconfig eth0 add 2002::1/64
```


> How to enable gateway for IPv6 in Ubuntu?
For IPv6 routing, there is a package called radvd that you can install on Linux. That stands for Route ADVertising Daemon, and it will advertise the fact that it is an IPv6 router other hosts. No need for DHCP. If there are only 2 networks, this should be all you need. Other hosts will find your router and use it.

> Router may require to do send Neighbor advertisement for Host Neighbor solicitation . 
That's all part of standard IPv6 operation. No configuration (other than an IP address) required.

If you need your Ubuntu router to exchange routing info about other networks with other routers then you will need to also start some other routing processes, but I don't know the name of them or how to configure them. But you could google for "linux" and the name of the routing protocol you want to use, such as OSPF, BGP, ISIS.

---

