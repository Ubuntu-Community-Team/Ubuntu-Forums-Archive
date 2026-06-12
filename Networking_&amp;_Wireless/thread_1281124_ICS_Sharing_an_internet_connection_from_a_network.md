---
title: "ICS: Sharing an internet connection from a network"
date: 2009-10-02
forum: Networking &amp; Wireless
---

### Post by jpaugh64 on 2009-10-02
While I will eventually figure out how to do this, I don't know enough to know whether my "solution" will adversely affect the campus network. Could you help me with either of these goals?

The deal:
I have two linux boxes:
   * (client) with Ubuntu 8.04
   * (host) with Ubuntu 9.04

The host has several network cards. eth1 is connected to my college's campus-wide network, which provides internet access. eth3 is connected to the client computer.

I have tried following this step-by-step guide ([https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)), but I still cannot access the internet from the client computer.

I have two restrictions to the possible implementations:

* The setup I use CANNOT adversely affect the outside network in any way: I have the greatest respect for our IT guys, and I don't want them mad at me, besides.
* The client needs to obtain an IP address dynamically: I will need to connect to other networks at other places.

I can connect the host to the company network (and the internet), and I can connect my client computer to the host, with DHCP working, but the client cannot access the internet. I suppose I should note that I deviated somewhat from the tutorial: I did not set up the client with a static IP before adding DHCP service. (If all else fails, I'll resort to that.)

Here is a summary of what my current setup should be:

Host configuration:
===================
eth1 -- connection to company network, and the internet     #verified
eth3 -- DHCP server for client--assigns addresses on the subnet 192.168.0.*   #verified

Rules added to iptables:
------------------------
```
iptables -A FORWARD -i eth1 -o eth3 -s 192.168.0.0/24 -m conntrack --ctstate NEW -j ACCEPT
iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
iptables -A POSTROUTING -t nat -j MASQUERADE 

sudo echo 1 > /proc/sys/net/ipv4/ip_forward
```

DNS & DHCP daemon: dnsmasq

Note: I also added this bug-fix to /etc/sysctl.conf, taking it on faith from the tutorial that it was necessary.

```
net.ipv4.conf.default.forwarding=1
net.ipv4.conf.all.forwarding=1

```Client configuration
====================
none

---

### Post by Iowan on 2009-10-04
When the client connects to the host, check (on client) **route** and contents of */etc/resolv.conf*. You may need to set up DHCP server to pass on the information (or set some of it via */etc/dhcp3/dhclient.conf*).

---

### Post by kevdog on 2009-10-04
From the client, can you ping the gateway?  Can you give us a few more details about your setup or are they exactly what is described in the tutorial?

---

### Post by jpaugh64 on 2009-10-05
My setup is very similar to what is described in the tutorial; however, I used a straight cable rather than a crossover cable. However, since, yes, I am able to ping the host, I didn't think that that would be a problem.

When I tried to ping a known server on the internet from the client, however, it failed. A buddy of mine suggested that perhaps ICMP forwarding was turned off (thus, ping would not work from the client), but that perhaps I could still use other protocols. 

I am going to try other protocols (basically, just opening my web browser), and also try using a crossover cable. In the process, I will check the route command, and the /etc/resolv.conf file. I will post my progress here.

---

### Post by jpaugh64 on 2009-10-05
I got it to work! Yea! Both ICMP and HTTP, at least. I assume most other protocols should work (other than those that just don't play well with NAT). 
On the client, the /etc/resolv.conf file has one line:
```
nameserver 192.168.0.1
```which, of course, indicates my host as its nameserver, which resolves host names for the client. 

And here is the output of the route command:
```
$route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth0

```(These two bits may seem superfluous now, but at least it is an example of what does work.)
I am still using the straight cable, so either my network card or the software that handles the client connection was able to work around that issue auto-magically. 

Part of the trouble that I had, I think, is that when I started dhclient, it took over eth3 and tried to get an IP address for it dynamically, when I had just set it to what I needed: 192.168.0.1 I know there is a way to limit dhclient, so after I've read it's man page, I should be able to get that detail taken care of.

(I am hoping that there is not a more serious issue: this host server has at least 2 ethx interfaces that only work intermittently; if this is a software issue, then it is probably the real sorce of my problem to begin with.)

Thanks to all who looked at this problem. I suppose I should mark it as solved? I am still willing to answer questions about this situation however, either to help someone else or to satisfy another's curiosity.

_**Edit:**_
I should note that this is not a complete fix. dhclient kicks the gateway off of the private network whenever that interface (eth3, in my case) has been inactive for a while. I will have to customize dhclient by modifying /etc/dhcp3/dhclient.conf--I'm hoping that this file will allow me to set up eth3 with a static IP, so the dhclient will do that forme instead of using ifconfig (only to have it undone by dhclient).

---

