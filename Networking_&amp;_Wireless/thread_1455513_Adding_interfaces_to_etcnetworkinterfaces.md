---
title: "Adding interfaces to /etc/network/interfaces"
date: 2010-04-16
forum: Networking &amp; Wireless
---

### Post by anjanesh on 2010-04-16
If I try to add a new interface (eth1) to /etc/network/interfaces, I get
```
 * Reconfiguring network interfaces...                                                                                                                                           SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
SIOCSIFBRDADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Failed to bring up eth1.
```
I had to comment out the previous eth0 and recreate the new one with eth0
```
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet static
#address 192.168.10.243
#netmask 255.255.255.0
#network 192.168.10.1
#broadcast 192.168.10.255
#gateway 192.168.10.1

auto eth0
iface eth0 inet static
address 192.168.1.243
netmask 255.255.255.0
network 192.168.1.1
broadcast 192.168.1.255
gateway 192.168.1.1
```
How do I add 2 interfaces and get anyone of them to work, as available ?

---

### Post by terazen on 2010-04-16
Do you have an eth1 or just eth0 and you want 2 ip addresses?  If you only have 1 nic then something like this may work.

auto eth0
iface eth0 inet static
address 1.1.1.10
netmask 255.255.255.0
gateway 1.1.1.1

auto eth0:0
iface eth0:0 inet static
address 1.1.1.20
netmask 255.255.255.0
gateway 1.1.1.1

---

### Post by anjanesh on 2010-04-19
Oh...ok, so an additional eth**x** would mean additional NIC ?
Yes, one NIC but may change ISPs via the routers quite often resulting in different gateways.
Thanks

---

### Post by terazen on 2010-04-20
What do you mean by "changing isp's quite often"?  Why would a default gateway change on the server instead of letting the router make the decision of which WAN connection to use?  I'm not sure I understand.

---

### Post by anjanesh on 2010-04-20
> Why would a default gateway change on the server instead of letting the  router make the decision of which WAN connection to use?
Two different routers - one for each ISP. Thats how its setup in office. The network guy will switch to another router when one is down.

---

### Post by terazen on 2010-04-20
Ah, I'm not sure how to setup something like that through the server's network setup.  There are options if your network guy can setup the routers differently though.

Option 1:  Setup the 2 routers so that the lan interface ip information is the same on both (only 1 of the lan interfaces can be connected at one time).  That way the default gateway would always stay the same when he/she moves the cable over.  The network person would know if this is possible.

Option 2:  Connect the 2 routers to each other and let a routing protocol do the failover automatically.

Option 3:  Connect a router to both internet connections (or both routers) and let it do the failover when one of the internet connections goes down.

I can't think of any way to do it solely through the server setup.

---

