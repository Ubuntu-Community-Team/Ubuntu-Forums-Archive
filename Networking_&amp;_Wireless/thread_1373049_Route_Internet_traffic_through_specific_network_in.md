---
title: "Route Internet traffic through specific network interface?"
date: 2010-01-05
forum: Networking &amp; Wireless
---

### Post by DarkBabar on 2010-01-05
I have a server running Ubuntu with two network interfaces. The first one (eth0) I'd like to use for the internal network, and the other one (eth1) is for the Internet. My problem is that connections to the Internet are routed through eth0, which is for internal network only. I would like for all connections to the Internet to go through eth1 and not even try eth0.

---

### Post by changingstate on 2010-01-05
Something along the lines of :

route add default dev eth1
route add -net <address> netmask <subnet mask> dev eth0

should work if I remember correctly.

---

### Post by vikrant82 on 2010-01-05
Well, once I did something like this.

Go [here]("http://kakku.wordpress.com/2007/11/03/combine-two-connections-for-a-single-torrent-download-routing-through-multiple-uplinks/")

---

### Post by doas777 on 2010-01-05
just make sure that the only route to 0.0.0.0/32 is through eth1. just to clarify, your gatway is upstream from eth1, and is on a different network from the network on eth0, right?

---

### Post by pricetech on 2010-01-05
What works for me is to simply not assign a gateway to my second interface, then add the necessary manual routes for the connections that have to use it.

---

### Post by DarkBabar on 2010-01-05
This really baffles me. My routing table used to look like this, and packets would always take the route through eth0.
```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
89.X.X.X        *               255.255.255.192 U     0      0        0 eth1
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
default         c-89-X-X-X.     0.0.0.0         UG    100    0        0 eth1
```
I changed it to this:
```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         *               0.0.0.0         U     0      0        0 eth1
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
default         89.X.X.X        0.0.0.0         UG    100    0        0 eth1
```
Now I'm not getting out at all. What am I doing wrong?

---

### Post by doas777 on 2010-01-05
when you are done, you need to have exactly one gateway (UG route to 0.0.0.0)
as it stands now, you have two default gateways defined, one for each interface.

is the 89 network between eth1 and the ISP equipment (modem/router device)? perhaps a simple network map would help

---

### Post by DarkBabar on 2010-01-05
My network looks like this.
[IMG]http://pici.se/pictures/QymQMzNMQ.png[/IMG]
I don't know how to make it any simpler while still keeping the functionality.

---

### Post by pricetech on 2010-01-05
Your ISP allows you to use a switch and get two IPs from them ??  Unusual, but if it works......

You want ETH1 to have Internet access, right ??  It's probably DHCP, which is fine as far as connectivity goes.  You'll get a default gateway from the ISP, so that should just plain work.

Your ETH0 should have a manual configuration.  Pick an IP that's outside of your router's DHCP pool and assign it manually to ETH0.  Include the subnet mask but leave the default gateway entry empty.

From the diagram everything else will be on the same subnet so you won't need to add any manual routes.

---

### Post by doas777 on 2010-01-05
is the switch really a switch(are both 89.x.x.x networks the same network)?

your topology has multiple paths to 0.0.0.0 so you will either have to route the traffic or adjust your topology. I think the problem with the routing is the default route to the interior router. you don't want a default gateway on that network, since it will pass your traffic the wrong way. 

if you are open to changing  the links a little, one option would be to see if your router has DMZ features, and to just connect it to the 192.168 network as a DMZ host.

---

### Post by DarkBabar on 2010-01-06
As advised, I removed the default route using
$ sudo route del -net default
going from this:...
```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
89.X.X.X        *               255.255.255.192 U     0      0        0 eth1
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
default         c-89-X-X-X.     0.0.0.0         UG    100    0        0 eth1
```
...to this:
```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
89.X.X.X        *               255.255.255.192 U     0      0        0 eth1
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         c-89-X-X-X.     0.0.0.0         UG    100    0        0 eth1
```
Now everything seems to work as intended. Thank you very much for your time and effort in helping me! Now one last thing. How do I make the changes stick?

---

### Post by doas777 on 2010-01-07
well, how do you configure your network, via the network manager? if so, you can apply custom routes there, and also set your gateways. just set the undesired gateways to blank.
if you use your interfaces file, then remove any undesired gateways, and list your routes there as described here: [http://www.ubuntugeek.com/howto-add-permanent-static-routes-in-ubuntu.html](http://www.ubuntugeek.com/howto-add-permanent-static-routes-in-ubuntu.html)

---

### Post by madzieph on 2011-07-31
Rather than opening a new thread, I hope I will be allowed just to continue the discussion with a little twist.

I would like to be able to do the same thing on my debian squeeze which acts as my multiwan router and torrent box.

I have 3 uplinks... a DSL with dynamic public ip and 2 wireless (via Motorola Canopy) on a private ip network with a shared public ip address.

The setup is fine except when accessing/downloading as free user from sites like rapidshare, filesonic, hotfile,etc. I do most of my downloading using torrent and having a premium subscription to these sites is not really an option for me.

It happens that sometimes I get connected to these sites via the wireless uplinks which because of the shared nature of the public ip, someone else could be downloading or has just finished their downsloads thereby I have to wait or get interrupted when another free user tries to access their system.

What I want to do is to be able to redirect all requests from my LAN to the interface connected to the dsl line. Now, this would have been easy if such sites only has 1 ip address or at least  on a single range because I could simply add an entry to the hosts file and to the static routing table. Each time I do a ping, I would get a different response from another ip and/or url.

Is there a way for me to be able to do the redirection?

Thanks in advance.

---

