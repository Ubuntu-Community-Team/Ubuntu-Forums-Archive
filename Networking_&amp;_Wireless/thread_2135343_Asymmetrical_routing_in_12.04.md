---
title: "Asymmetrical routing in 12.04"
date: 2013-04-14
forum: Networking &amp; Wireless
---

### Post by Coogan on 2013-04-14
I've got multiple NICs in my Ubuntu server; two (eth0, eth2) are on the same network.  Until today, I was running 10.04 server and had fixed the problem of asymmetrical routing by using the steps in [this article]("http://www.linuxjournal.com/article/7291?page=0,1").  Basically, I added the following to the kernel routing table:

```

> ip route add default via 192.168.1.140 dev eth0 tab 1
> ip route add default via 192.168.1.140 dev eth2 tab 2
> ip rule add from 192.168.1.100/32 tab 1 priority 500
> ip rule add from 192.168.1.102/32 tab 2 priority 600

```

Briefly, the setup.

192.168.1.100: eth0
192.168.1.102: eth2 (eth1 is inactive)
192.168.1.140: Gateway

Using the ip routing changes above I was able to segregate traffic - responses to data coming in eth0 goes out eth0, and responses to data coming in eth2 goes out eth2.  Easy.

This no longer appears to work now that I've upgraded to 12.04.  The *ip route* commands are taken, but only the first one entered seems to take effect - whichever one is entered second is seemingly ignored:

*ip route show*
```

default via 192.168.1.140 dev eth0 
169.254.0.0/16 dev eth2  scope link  metric 1000 
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.100 
192.168.1.0/24 dev eth2  proto kernel  scope link  src 192.168.1.102

```

*ip route show table 1*
```

default via 192.168.1.140 dev eth0

```

*ip route show table 2*
```

default via 192.168.1.140 dev eth2

```

*netstat -anr*
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.1.140   0.0.0.0         UG        0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth2
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth2

```

As shown above, only one interface (eth0) can get outside my LAN.  The other interface (eth2) can connect inside the LAN, but cannot leave the network.

So I've really got two problems - asymmetrical routing, and only one interface can leave the network.  Both were solved with some simple commands in 10.04, but these no longer work in 12.04.

I've googled a lot for the in the last few hours, but nothing seems to be working.

Coogan

---

### Post by sauyon on 2013-04-14
You could add a gateway to eth2's routing entry instead of telling it to use the default:
```
ip route change 192.168.1.0 via 192.168.1.140 dev eth2
```

---

### Post by Coogan on 2013-04-14
> **sauyon said:**
> You could add a gateway to eth2's routing entry instead of telling it to use the default:
```
ip route change 192.168.1.0 via 192.168.1.140 dev eth2
```

Doesn't seem to work:

[I]> ip route change 192.168.1.0 via 192.168.1.140 dev eth2
RTNETLINK answers: No such file or directory[/I]

Here's the content of /etc/network/interfaces, btw:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.0.255
gateway 192.168.1.140

auto eth2
iface eth2 inet static
address 192.168.1.102
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.0.255

```

---

### Post by Coogan on 2013-04-14
Well, this didn't work:

```

> ip route add default via 192.168.1.140 dev eth0 tab 1
> ip route add default via 192.168.1.140 dev eth2 tab 2

```

But this did:

```

> route add default gw 192.168.1.140 dev eth0 table 1
> route add default gw 192.168.1.140 dev eth2 table 2

```

Now it's working as before.

```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.1.140   0.0.0.0         UG    0      0        0 eth2
default         192.168.1.140   0.0.0.0         UG    0      0        0 eth0
169.254.0.0     *               255.255.0.0     U     1000   0        0 eth2
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth2

```

I'm guessing something has changed with the iproute2 package in 12.04?

---

### Post by sauyon on 2013-04-14
Nevermind then :P

---

