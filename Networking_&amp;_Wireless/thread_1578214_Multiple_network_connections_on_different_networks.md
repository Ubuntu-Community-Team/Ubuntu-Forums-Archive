---
title: "Multiple network connections on different networks"
date: 2010-09-20
forum: Networking &amp; Wireless
---

### Post by dimoss on 2010-09-20
Hi,

I am total newby in Ubuntu 10.04. I have just installed it in my office where I have two networks card one connect to a router giving the internet access and the other connected to the windows based work network providing access to the work network sources. In XP everything works fine as I can keep both connections alive and have the results I want.

However although I don't know how to do it in Ubuntu 10.04.
Till now I have setup the first connection directly to my router and I have internet access but I cannot set the other one.

Another question is how I can force ubuntu to use the router connection as the default one when I log in.

Thanks,

Denis

---

### Post by SeijiSensei on 2010-09-20
If you connect the second interface to the office network, does it get an address via DHCP from the Windows server?  If so, you need to add a "route" on the Ubuntu box telling it to use that interface to reach the internal network.  

First, open the Terminal, and with only the Internet router connected, type the command "ifconfig".  You should see the machine's IP address assigned to the interface called "eth0".  Now plug in the cable to the internal network and type ifconfig again.  Do you see an entry for eth1?  If so, what address does it have?

If both interfaces are up and have addresses, then type the command "route -n".  This will tell you how packets are routed over the two networks.  Let's suppose your Windows-side interface (eth1) has address 192.168.1.100, and your Internet side (eth0) has address 10.1.1.2.  In this case, your routing table should include some lines that look like this:

```
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
10.1.1.0        0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         10.1.1.0        0.0.0.0         UG    0      0        0 eth0
```

This says that packets intended for 192.168.1.0 (the Windows network in your case) should be sent out eth1, while everything else (0.0.0.0) will be sent to the Internet router via eth0.  If you don't see an entry for the Windows network using eth1, then you'll need to add the route manually.  

You can fix this by creating a file in /etc/network/if-up.d/ like this:

```

/sbin/ip route add 192.168.1.0/24 dev eth1

```

Replace 192.168.1.0 with the appropriate network address for your Windows network.  It usually will be the same as the interface IP address with the last numeral replaced by zero.  You should do this as the "root" (administrative) user, by typing the command "sudo nano /etc/network/if-up.d/myinsideroute" and entering your password when prompted.

You'll need to mark the script executable by entering the command "sudo chmod 0744 /etc/network/if-up.d/myinsideroute".

> **dimoss said:**
> Another question is how I can force ubuntu to use the router connection as the default one when I log in.

The easiest solution is make sure the router is connected to the interface called eth0.  If the Internet router is attached to eth1, switch the cables.

---

### Post by dimoss on 2010-09-20
Hi,
Thanks for the reply.
Let's make it more clear.

I have put the ip manually to the internet connection (router). This is
ip: 192.168.2.2
mask: 255.255.255.0
gateway: 192.168.2.1
dns: 208.67.222.222, 208.67.220.220

The internal windows network connection (internal network) configuration is:
Automatic DHCP (addresses only)
dns: 10.10.1.2, 10.10.1.3

**Can you show me how to make the route table again?**

As for the default I understood that I have to change the cables in order to make my router connected to eth0

Thanks,

Denis

---

### Post by SeijiSensei on 2010-09-20
> **dimoss said:**
> **Can you show me how to make the route table again?**

I take it the static definition for the Internet side, and the "auto" definition for eth1, are in /etc/network/interfaces?  If so, you'll just need an executable script in /etc/network/if-up.d/ which reads:

/sbin/ip route add 10.10.1.0/24 dev eth1

> As for the default I understood that I have to change the cables in order to make my router connected to eth0

Well, in principle, it doesn't matter as long as all the configurations are correct.  I find it easiest to think of eth0 as the "external" interface and eth1 as the "internal" interface.  Is the definition for 192.168.2.2 assigned to eth0 in /etc/network/interfaces?  What's more important, actually, is the interface that points to the default route, which you have correctly set to use the Internet router.  So essentially it sounds like you've got everything in place except a route to the 10.10.1.0/24 network (10.10.1.0/24 => 10.10.1.0/255.255.255.0).

If you still need help, can we see the contents of /etc/network/interfaces and the results of the command "route -n"?

---

### Post by dimoss on 2010-09-21
> **SeijiSensei said:**
> I take it the static definition for the Internet side, and the "auto" definition for eth1, are in /etc/network/interfaces?  If so, you'll just need an executable script in /etc/network/if-up.d/ which reads:

/sbin/ip route add 10.10.1.0/24 dev eth1



Well, in principle, it doesn't matter as long as all the configurations are correct.  I find it easiest to think of eth0 as the "external" interface and eth1 as the "internal" interface.  Is the definition for 192.168.2.2 assigned to eth0 in /etc/network/interfaces?  What's more important, actually, is the interface that points to the default route, which you have correctly set to use the Internet router.  So essentially it sounds like you've got everything in place except a route to the 10.10.1.0/24 network (10.10.1.0/24 => 10.10.1.0/255.255.255.0).

If you still need help, can we see the contents of  and the results of the command "route -n"?

Hi again,

I need help!

The content of the /etc/network/interfaces is:
auto lo
iface lo inet loopback

The result of the command "route -n" is:

```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
10.10.1.0       0.0.0.0         255.255.255.0   U     1      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         10.10.1.60      0.0.0.0         UG    0      0        0 eth1

```The eth0 is the external connection (router).
The eth1 is the internal connection (windows)

Both are active and both can have Internet access but I prefer to have Internet access from the router and not the windows network. Another problem is that the eth1 is always default and I cannot change that even if I change the cables. When I tried to change the cables I haven't Internet access.
I haven't add any static route yet or something else.

Any ideas?

Thanks again for your help..

Denis

---

### Post by SeijiSensei on 2010-09-21
It looks like dhclient is taking the routing information from the DHCP server and pointing the default route to 10.10.1.60.  Unfortunately it appears that the default routing is not a parameter you can override manually in dhclient.conf.

You could run a script after bringing up the network that looks like this:

```

ip route del default
ip route add default via 192.168.2.1

```

That's about all I can think of at the moment.  I'll let you know if I have any other ideas.

---

