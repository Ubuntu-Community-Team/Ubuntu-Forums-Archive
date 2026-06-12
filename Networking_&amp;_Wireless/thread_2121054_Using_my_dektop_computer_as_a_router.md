---
title: "Using my dektop computer as a router"
date: 2013-02-28
forum: Networking &amp; Wireless
---

### Post by grizdog on 2013-02-28
It's possible this is covered in one of the 12.04 threads, but I couldn't find anything that seemed similar.  I haven't used wireless in my house for a long time, I don't know which version of Ubuntu it last worked for, but it did work for Ubuntu at one time.

My desktop computer is an old custom lashup with some sort of Intel motherboard with an on-board network connection (eth1) and a network card (eth0).  The network signal from my ISP comes out of the wall, into the modem and then into eth0.  eth1 is connected to a wireless access point (linksys WAP54G) And I had it set up to use the private 192.168.1 network for wireless connections.  The idea was that I had the iptables on my desktop computer providing a firewall for everything, and iptables also handled NAT for the private network.  When I last used it, several years ago, it worked fine.  Now, when I turn on eth1, the network hangs - can't ping anything outside of the house, and incidentally, it also can't find the new wireless printer I just plugged in, but we'll get to that after the basic problem is solved.

Here are the lines in my iptables config file that provide the NAT (and these have changed several times over the years - I may have to change them again:

```

iptables -A FORWARD -o eth1 -i eth0 -s 192.168.1.0/24 -m conntrack --ctstate NEW -j ACCEPT
iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
iptables -A POSTROUTING -t nat -j MASQUERADE

```

and here is the routing table (output from the `route' command) with eth1 disabled:

```

default         24-117-84-1.cpe 0.0.0.0         UG    0      0        0 eth0
24.117.84.0     *               255.255.254.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0

```

And here it is with eth1 enabled:

```

default         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
24.117.84.0     *               255.255.254.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
192.168.1.0     *               255.255.255.0   U     1      0        0 eth1

```

It seems like I just need a little tweak to the routing table, something I could probably do manually, but I'd like to get an organic understanding of this, rahter than patch a bad configuration.  If the time has come to get a wireless router like everyone else, I'm willing to do that, but this has worked and I sitll like the idea of controlling the firewall with iptables.

Thanks for any help.

Alex

---

### Post by beejee on 2013-03-01
Heya, don't mind Schnappi1989, probably a spammer getting his postcount up. He'll be banned by the time he reaches 25 posts :)

Can you post your /etc/network/interfaces to see the way the network is set up?

If you configured the network via network-manager /etc/networks/interfaces will not contain a lot of info and you will have to look it up via the graphical interface.(I haven't ever set up routing this way but i'm sure we can find out)
Rightclick and choose edit on network manager,  choose one of the connections, than edit. In the IPv4 tab there is a button routes. What info is in there for both your connections?

---

### Post by grizdog on 2013-03-01
Looks like Schnappi wore out his welcome pretty quickly - thanks for replying.

Here is /etc/network/interfaces:
```

 cat /etc/network/interfaces 
auto lo
iface lo inet loopback

```
As for the information from network manager, both interfaces had absolutely nothing.  there was a dialogue area, with 4 tabs: address, netmask, Gateway, Metric.  All four were empty - I even looked at IPV6, empty there too (as I would have expected)

Thanks for taking an interest

Alex

---

