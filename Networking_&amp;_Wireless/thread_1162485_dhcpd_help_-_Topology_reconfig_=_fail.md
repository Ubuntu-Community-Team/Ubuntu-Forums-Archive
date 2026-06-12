---
title: "dhcpd help - Topology reconfig = fail"
date: 2009-05-17
forum: Networking &amp; Wireless
---

### Post by infallible on 2009-05-17
I've decided to route my home network through my desktop box, mostly to learn and prioritize connections but also to get draconian on a few leech wireless clients with ntop and some creative resolving. Currently, the network looks like this, with the modem bridged and router performing ISP authentication:

Internet -> DSL Modem -> Router 
-(WAN)->Wireless Clients
-(eth1)->Server 

I think I want it to be like this, with the modem still bridged but to the server:

Internet-> DSL Modem -(eth0)-> Server -(eth1)-> Router -(WAN)-> wireless clients

I ignorantly threw myself into several different approaches here. I first tried setting up dhcpd on the server and wiring it to the uplink on the router; it didn't work. I'm assuming I just don't know how to configure a dhcp server.

I also have a gigabit switch en route. At first it won't do much, but I have a second 'server' in the works for some sweet, hot clustering action. I'll be following the blueprint at [https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide]("https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide"), so I know I'll need to learn more about DHCP. At that point, I'll probably use the modem's usb port, assuming compatibility, and dedicate an ethernet port and subnet to the cluster and another of each to server functions. 

Right now, I don't really understand why dhcpd didn't work for me. I used the default dhcp.conf, and added 
```

subnet 10.0.0.0 netmask 255.0.0.0 
#will these numbers work?
{
  range 10.0.0.100 10.0.0.150;
  option domain-name-servers 208.67.222.222, 208.67.220.220; 
#open DNS - trying to avoid learning bind for now
  option domain-name "rutherford.mesistopheles.org";
   option broadcast-address 10.0.0.255;
#is this an arbitrary value?
  default-lease-time 600;
  max-lease-time 7200
}

```
I had first set the router statically to 10.0.0.105. I ran a cable from eth1 to the uplink on the router, and network manager showed a connection. With dhcp disabled on the router, it wouldn't negotiate wireless clients. with dhcp on the router enabled, no internet on the wireless clients.
  
I know I must be leaving out some crucial steps. I appreciate having my windy post read, and I'm hoping someone can point me in the right direction.

---

### Post by superprash2003 on 2009-05-18
here's a guide on dhcp [http://www.prash-babu.com/2009/05/how-to-enable-dhcp-server-in-ubuntu.html](http://www.prash-babu.com/2009/05/how-to-enable-dhcp-server-in-ubuntu.html)

---

