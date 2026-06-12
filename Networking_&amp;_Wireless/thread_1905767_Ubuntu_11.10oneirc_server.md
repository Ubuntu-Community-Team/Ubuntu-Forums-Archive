---
title: "Ubuntu 11.10/oneirc server"
date: 2012-01-07
forum: Networking &amp; Wireless
---

### Post by bjorne67 on 2012-01-07
Hello!

have some problem with my /etc/network/interfaces and i don't now how i fix that...
looks to be same nasty problem in centos 6.2...

I have in my interfaceses:
auto eth0
iface eth0 inet static
        address 192.168.0.11
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1

auto eth0:0
iface eth0:0 inet static
        address 172.16.1.11
        netmask 255.255.255.0
        network 172.16.1.0
        broadcast 172.16.1.255

and when i run ifconfig, i get up only eth0

eth0      Link encap:Ethernet  HWaddr aa:aa:aa:aa:aa
          inet addr:192.168.0.11  Bcast:192.168.0.255  Mask:255.255.255.0

where are eth0:0 somewhere? 

and i can ping 172.16.1.1 from that computer and some other on 172.16.1.x network
and i don't see that on ifconfig....

Can someone help me with this? and tell me if this are a bug or what?

//bjorne

---

### Post by Iowan on 2012-01-09
I stumbled across [this]("http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/"). 
Just for grins, try changing it to eth0:1 instead of eth0:0.

---

### Post by bjorne67 on 2012-01-11
I have try to change to eth0:1-9 :) and i got this error in oneiric and precise
not in 11.04...

//bjorne

---

### Post by aztekk on 2012-01-11
There is a bug with adding aliases to a single NIC in oneiric.

[https://bugs.launchpad.net/ubuntu/oneiric/+source/ifupdown/+bug/876829](https://bugs.launchpad.net/ubuntu/oneiric/+source/ifupdown/+bug/876829)

---

