---
title: "Routing over Aliased IP addresses"
date: 2013-04-20
forum: Networking &amp; Wireless
---

### Post by dawbomb on 2013-04-20
Hi All,

Due to people in my house (I suspect my brother) abusing our internet regularly, slowing it down terribly for everyone else, I want to route all traffic through my Ubuntu Server so that I can monitor the bandwidth usage of everyone on the network.

Our network setup is as follows:

```

                                                           ----  Switch  -------  Smart TV, Destkop, Raspberry Pi
                                                          |
Internet -------- Netgear ADSL router/AP -------  Laptops
                                                          |
                                                           ----  HP Proliant MicroServer
```

On the server, the network config is as follows:
```
auto eth0
iface eth0 inet static
   address 192.168.0.2
   gateway 192.168.0.1
   netmask 255.255.255.0
   network 192.168.0.0
   broadcast 192.168.0.255

auto eth0:0
iface eth0:1 inet static
   address 192.168.1.1
   network 192.168.1.0
   netmask 255.255.255.0
   broadcast 192.168.1.255
```

I've got the DHCP and DNS servers running on the server happily.  Now all I need to do in order to get this bad boy working is to set up the routing, which is proving more difficult than I originally thought it would be, because iptables doesn't seem to like the idea of working with virtual interfaces.

I've followed a couple of guides on the net, and have got absolutely nowhere.  The syslog shows that it's doing something, but the browser on the computers on the network just time out.  The logs that I get are like so:
```
Apr 20 13:57:09 ****-server kernel: [ 3625.186727] IN=eth0 OUT=eth0 MAC=****  SRC=192.168.1.3 DST=108.160.162.44 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=18723 DF PROTO=TCP SPT=59277 DPT=80 WINDOW=14600 RES=0x00 SYN URGP=0
```

Any idea what I can do, short of going out and buying a second NIC?  I've got a spare one, but it's PCI, and my server needs PCIe.  And I'm a student, so I'm trying to avoid spending the cash unless I have to :-P

Thanks!

---

### Post by The Cog on 2013-04-20
I guess your netgear router is 192.168.0.1. 
Does it know that it can reach network 192.168.1.x via 192.168.0.2? You have to add a static route into the netgear to tell it this, or it won't forward reply packets to you.

Alternatively, you can configure ip address translation in your server so that all traffic from network 192.168.1.x appears to have come from 192.16.8.0.x, but there is a risk of a clash here so I don't recommend it.

If you do any filtering in iptables, you will have to do it by IP address rather than by interface, since there is really only one interface (it just has multiple addresses).

It's probably easiest to use tcpdump to try to see what's going on:
```
sudo tcpdump -n
```

---

### Post by dawbomb on 2013-04-20
Aah!  I didn't even think to set up a static route on the Netgear router.  Thanks, that did the job!

---

### Post by dawbomb on 2013-04-20
Because I've seen quite a number of unanswered threads about a router with an Aliased IP address, here's the solution:

Assuming that your Ubuntu router is at 192.168.0.2 on the external network (eth0), and at 192.168.1.1 on the internal network (eth0:0), run the following as root:
```

echo "1" > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -o 192.168.0.2 -j MASQUERADE
iptables -A FORWARD -i 192.168.0.2 -o 192.168.1.1 -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -i 192.168.1.1 -o 192.168.0.2 -j ACCEPT
```

And then don't forget to set up a static root on your internet gateway (if you have one):
```

Destination IP address:  192.168.1.0
IP Subnet Mask:  255.255.255.0
Gateway IP address:  192.168.0.2
Metric:  2
```

---

### Post by The Cog on 2013-04-20
That has me confused. Do you really need both the static route and the masquerade? By my understanding of things, you should onle need one or the other. 

I thought:
If you are masquerading the  router won't talk to anything from 192.168.1.x so the static route is not need.
If you have the static route, the router knows how to send back to 192.168.1.x so masquerading isn't needed.
Am I missing something, or are you implementing 3 fixes when you only need one?

---

### Post by dawbomb on 2013-04-28
> **The Cog said:**
> That has me confused. Do you really need both the static route and the masquerade? By my understanding of things, you should onle need one or the other. 

I thought:
If you are masquerading the  router won't talk to anything from 192.168.1.x so the static route is not need.
If you have the static route, the router knows how to send back to 192.168.1.x so masquerading isn't needed.
Am I missing something, or are you implementing 3 fixes when you only need one?

What I'm doing now is 
```
sudo iptables -A FORWARD -s 192.168.0.2 -d 192.168.1.1 -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A FORWARD -s 192.168.1.1 -d 192.168.0.2 -j ACCEPT
```

That's been working perfectly.  Happy days!  

Now the next step is to get a transarent proxy server going too.  Which sort of works.  It works for some websites, but not all, and the websites it does work for are painfully slow.  Sites hosted internally only work if you use the FQDM, not the IP address, so I suspect that it's routing things circularly, but I don't know how to get away from that.  Any ideas?

I tried setting up the proxy server to only listen on 192.168.1.2 (another IP alias on the same server), but that hasn't change anything.

Current rules that I'm using are (the above two plus):
```
sudo iptables -t nat -A PREROUTING -s 192.168.1.0/24 -p tcp --dport 80 -j DNAT --to-destination 192.168.1.2:3128
sudo iptables -t nat -A POSTROUTING -s 192.168.1.0/24 -p tcp --dport 3128 -o 192.168.0.2 -j MASQUERADE
```

---

### Post by dawbomb on 2013-04-28
In fact, I think that I'm somehow bypassing the proxy completely, as it's not logging very much at all.  And everything that it does log is returning 0 bytes with status code 400.  So something isn't right here...

Edit:
HTTPS sites are the ones which still work <facepalm>

---

