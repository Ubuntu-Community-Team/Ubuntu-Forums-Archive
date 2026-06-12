---
title: "RTNETLINK answers: File exists problem ubuntu 12.04"
date: 2013-03-15
forum: Networking &amp; Wireless
---

### Post by Drenriza on 2013-03-15
Hi guys i have a ubuntu server 12.04 where i have configured two interfaces (need to configure 5 in total).
But when i restart the network it says

RTNETLINK answers: File exists.

What is it complaining about?
I cant really se anything in /var/log/syslog that could indicate the error.

My configuration looks as follows
```

auto lo eth0 eth1

iface lo inet loopback

iface eth0 inet static
address 172.16.1.10
netmask 255.255.255.0
network 172.16.1.0
broadcast 172.16.1.255
gateway 172.16.1.1

iface eth1 inet static
address 10.1.0.203
netmask 255.255.255.0
network 10.1.0.0
broadcast 10.1.0.255
gateway 10.1.0.1

```

If i comment out eth1 and its configuration, interface eth0 stats up just fine.
But when i un-comment eth1 and its config i get the error.

Even tho under ifconfig eth1 i can see the interface as configured with ip address, netmask and so on. But i cannot
sudo ifdown eth1 = ifdown: interface eth1 not configured.

ANYONE WHO CAN HELP ME
It is driving me crasy ,)

Thanks on advance.
Kind regards.

---

### Post by Drenriza on 2013-03-15
If anyone can help me with this, it would be greatly appreciated. Since i need the issue solved as quickly as possible :(

---

### Post by steeldriver on 2013-03-15
maybe udev is somehow assigning 2 names (both eth0 and eth1) to the same device? what does

```
cat /etc/udev/rules.d/70-persistent-net.rules
```

say?

---

### Post by Drenriza on 2013-03-15
> **steeldriver said:**
> maybe udev is somehow assigning 2 names (both eth0 and eth1) to the same device? what does

```
cat /etc/udev/rules.d/70-persistent-net.rules
```

say?


It's empty

Route -n has the output of
```

Destination     Gateway     Genmask     Flags Metric Ref Use Iface
0.0.0.0           172.16.1.1 0.0.0.0         UG    100     0   0     eth0
10.1.0.0         0.0.0.0      255.255.255.0 U      0      0   0      eth1
172.16.1.0     0.0.0.0      255.255.255.0  U     0      0    0    eth0

```

Is the above correct??

Why dont it get a 
0.0.0.0 10.1.0.1 0.0.0.0 UG 0 0 0 eth1 ??

EDIT
So fiddled around with it some more. And when i got the configuration as above, eth0 and eth1 activated.
It says RTNETLINK answers: File exist.

But under ifconfig you can see that eth1 got a ip, netmask and BC address.
route -n is above in the code snippet.

When i ping 172.16.1.10(ip address of eth0) i get a Request timeout for icmp_seq 0
When i ping 10.1.0.203(ip address eth1) i get a 64 bytes from 10.1.0.203: icmp_seq=0 ttl=64 time=0.660 ms.

If i remove eth1 config in /etc/networking/interfaces i cannot ping eth1 (ofcourse) and i can ping eth0 again

What on earth is going on........

---

### Post by Drenriza on 2013-03-15
122 views 1 reply :/

---

### Post by iponeverything on 2013-03-15
Only use gateway for one that you are using for default gw. 

Network is deduced from the mask so its unnecessary - and getting to an ip addresses on a known networks is done via arp. 

```

auto lo eth0 eth1

iface lo inet loopback

iface eth0 inet static
address 172.16.1.10
netmask 255.255.255.0

iface eth1 inet static
address 10.1.0.203
netmask 255.255.255.0

```

---

### Post by Drenriza on 2013-03-16
> **iponeverything said:**
> Only use gateway for one that you are using for default gw. 

Network is deduced from the mask so its unnecessary - and getting to an ip addresses on a known networks is done via arp. 

```

auto lo eth0 eth1

iface lo inet loopback

iface eth0 inet static
address 172.16.1.10
netmask 255.255.255.0

iface eth1 inet static
address 10.1.0.203
netmask 255.255.255.0

```

Sure but if leaving your own network you need a GW to point at. Thus it is their, since i got a address scope subnettet to 7 different vlans and divided into 7 different networks.

Tho does this not resolve my issue when setting up 2 different nics. Where i get the RTNETLINK answers: File exists. What causes this issue and how is it resolved?

---

### Post by Drenriza on 2013-03-16
Well i have tried in a virtual machine and on a physical machine and i cannot get two nics to work at the same time without the error. Is it that uncommon in Ubuntu server edition to have two nics?

---

### Post by iponeverything on 2013-03-16
> **Drenriza said:**
> Sure but if leaving your own network you need a GW to point at. Thus it is their, since i got a address scope subnettet to 7 different vlans and divided into 7 different networks.

You don't have a default gw for every interface. 

> **Drenriza said:**
> 
Tho does this not resolve my issue when setting up 2 different nics. Where i get the RTNETLINK answers: File exists. What causes this issue and how is it resolved?

let me give you clue here, since you clearly need one:  do a "man interfaces"

---

### Post by iponeverything on 2013-03-16
seriously - 

its quite easy to configure the interfaces by hand using the ifconfig and route commands - try it, and you will see where your "error" is.

---

### Post by Drenriza on 2013-03-18
> **iponeverything said:**
> seriously - 

its quite easy to configure the interfaces by hand using the ifconfig and route commands - try it, and you will see where your "error" is.

I configured the interfaces in /etc/network/interfaces.
You NEED!
IP
Netmask
Gateway
and network (it might be calculated automatically, but u still need it so it is their).

If their is a error in this because ubuntu has some weird setup, then just say so.
Instead of.

**let me give you clue here, since you clearly need one:  do a "man interfaces" **

The above is not helpfull. Since i already by hand configured the network.
And configuring a network by hand, is easy yes. Your telling someone who has used cisco equitment the past 5 years on the CCNA and CCNP level. 

And created a 3 layer network with 7 VLSM networks, several security layers, HSRP, fail over links, bundled links with load balancing, DMZ zone, RSTP and a interior gateway protocol and so on.
Which all works just fine.

But ty for the info.
**its quite easy to configure the interfaces by hand**

Edit
Ow ye. And the above is just my home test setup.

---

### Post by Drenriza on 2013-03-18
Solved my issue. Installed Debian core system and configured it as i wanted. No issues.

Obviously ubuntu is making some sort of issues for itself, which i dont have the patience to solve.
When it is unnecessary. so should i say, use a "real" server system instead?

---

### Post by iponeverything on 2013-03-18
glad you got it sorted.

---

### Post by atOregon on 2013-03-29
Drenriza, my config is almost exactly like yours with 2 nics statically configured. The "RTNETLINK answers: File Exists" message went away when I assigned a metric to the two interfaces. You can't have two default gateways with the same metric. See Stéphane's answer #8 at [https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/1043244](https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/1043244) 

Here's my /etc/network/interfaces
```
# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
# Note that a metric is required if multiple gateways are present
auto eth0
iface eth0 inet static
metric 0
address 172.16.1.4
netmask 255.255.255.0
gateway 172.16.1.1
dns-nameservers 172.16.1.3 208.67.222.222


# The secondary network interface
# Note that a metric is required if multiple gateways are present
auto eth1
iface eth1 inet static
metric 1
address 10.1.10.14
netmask 255.255.255.0
gateway 10.1.10.1
dns-nameservers 208.67.222.222 208.67.220.220

```

---

### Post by Drenriza on 2013-03-31
Thanks for your reply atOregon. But this just prove hos bad Ubuntu is to handle multiple interfaces. And ye, i would never chose ubuntu with a multi interface system.

---

### Post by geekman on 2013-06-07
> **Drenriza said:**
> Thanks for your reply atOregon. But this just prove hos bad Ubuntu is to handle multiple interfaces. And ye, i would never chose ubuntu with a multi interface system.

Wow. So when I saw this, I had to login just to argue what you're saying here, it's that ridiculous. Do you honestly think that Ubuntu is not capable of using multiple NICs? Really?? This is a core function of any OS networking stack. The fact you could say something like this - particularly that you imply that you need a "server" grade OS to do this, is crazy. 

I have none of the almighty certifications you claim to have, but it seems clear to me that you are missing some networking fundamentals. If this is working for you in Debian, but not Ubuntu, it is because Ubuntu is trying to protect you from doing something dumb, but Debian is not.

As atOregon says, by having to gateway definitions you're defining two routes with a destination prefix of 0.0.0.0/0.0.0.0 with an equal metric. If you do this, you will find your connectivity drops as the packets are sent between the two separate interfaces, fragmenting your traffic. If WAN load balancing is what you're trying to achieve (where you have multiple connections to the internet - or other WAN - and hence multiple internet gateways), then I suggest you look up that. Connection tracking is required for this to work properly, you can't just spam packets out with identical routes and have it work properly.

What others are trying to explain to you is that any traffic within the same subnet on a given interface is done via Layer 2 ARP broadcasts. For any subnet your PC is *directly* connected to there is no need for a gateway, and then you need to pick ONE interface to define your internet gateway which will act as the router between you and those subnets which you are not connected to. 

We do this with a setup of 30 VLANs, with one external, one internal interface, and it works! Even on Ubuntu!

If for some special reason you need to route traffic for external subnets out particular interfaces, then you should be defining your own static routes with the appropriate destination prefixes and setting the interface accordingly.

The answer is simple in this case: Ubuntu is fine. You are wrong.

Congratulations, your unfailing arrogance has caused me to bring up a dead post, and hate people on the internet just a little bit more.

---

