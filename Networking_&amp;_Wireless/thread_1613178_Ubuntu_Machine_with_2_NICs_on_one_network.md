---
title: "Ubuntu Machine with 2 NICs on one network"
date: 2010-11-04
forum: Networking &amp; Wireless
---

### Post by live4fun on 2010-11-04
[IMG]http://img823.imageshack.us/img823/6746/homenetworklayout.png[/IMG]


Hi,
please have a lock at the diagram i created for clarification.
I hope it aids in getting a fast overview of my setup. Thanks to everybody in advance who is taking the time to look at my problem. I tried to present the information as structured as possible.:KS


Problem: Howto Setup Routing on the Ubuntu Desktop.

**Goal/Szenario**

The part of drawing in the ellipse is always on. More specific fritzbox is always on and can wake on lan start the ubuntu desktop. The rest of the network outside of the ellipse (which is my gbit network) is powered off while i am not at home. When I am home I want to connect my Laptop to the Gbit-Switch and want to use Gbit network speed between my ubuntu desktop and laptop. While I am out only the minimum setup should be powered to keep the electricity bill low.

**Problem/Question**
I am not able to setup routing corretly on my ubuntu desktop.

**Current Approach**
Here is what I did to configure it like I thought it should work.

1. Looking at routing table after boot

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.11.12.0      *               255.255.255.0   U     0      0        0 eth0
10.11.12.0      *               255.255.255.0   U     0      0        0 eth1
default         fritz.box       0.0.0.0         UG    0      0        0 eth1
default         fritz.box       0.0.0.0         UG    0      0        0 eth0
```

2. Remove duplicate defaults routes on the two devices
```
route del default eth0
route del default eth0
```
3. Establish route to fixed ip of my router
```
route add -net default gw 10.11.12.13 dev eth1
```

4. Check new routing table
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.11.12.0      *               255.255.255.0   U     0      0        0 eth0
10.11.12.0      *               255.255.255.0   U     0      0        0 eth1
default         fritz.box       0.0.0.0         UG    0      0        0 eth1
```
Don't knwo why the ip again is resolved to fritz.box here. :confused:

5. Test connection 
But still i can't ping inet domains like google.de reliable. Some packages get dropped (missing sequence nbrs) :confused:

```
PING google.de (74.125.43.99) 56(84) bytes of data.
64 bytes from bw-in-f99.1e100.net (74.125.43.99): icmp_seq=30 ttl=50 time=52.6 ms
64 bytes from bw-in-f99.1e100.net (74.125.43.99): icmp_seq=31 ttl=50 time=52.6 ms
64 bytes from bw-in-f99.1e100.net (74.125.43.99): icmp_seq=32 ttl=50 time=52.3 ms
64 bytes from bw-in-f99.1e100.net (74.125.43.99): icmp_seq=33 ttl=50 time=52.7 ms
64 bytes from bw-in-f99.1e100.net (74.125.43.99): icmp_seq=34 ttl=50 time=52.6 ms
64 bytes from bw-in-f99.1e100.net (74.125.43.99): icmp_seq=35 ttl=50 time=52.7 ms
64 bytes from bw-in-f99.1e100.net (74.125.43.99): icmp_seq=36 ttl=50 time=53.1 ms
64 bytes from bw-in-f99.1e100.net (74.125.43.99): icmp_seq=37 ttl=50 time=52.5 ms
64 bytes from bw-in-f99.1e100.net (74.125.43.99): icmp_seq=66 ttl=50 time=54.1 ms
64 bytes from bw-in-f99.1e100.net (74.125.43.99): icmp_seq=67 ttl=50 time=52.8 ms
```


See my /etc/network/interfaces 
eth0 is the gbit connection to the switch
eth1 is the 100mbit connection to the fritzbox
```

#define initialization sequence of hardware devices
auto lo eth0 eth1
# The loopback network interface
iface lo inet loopback

# The primary network interface
iface eth0 inet dhcp
iface eth1 inet dhcp


```

If I can provide more information to aid you helping me please let me know.

Best Regards

---

### Post by grahammechanical on 2010-11-04
I am not an expert. I do not have any experience in setting up LANs but, if I have the correct understanding of what you are trying to do, you have set eth1 on the desktop as the default connection and have set it to connect to fritzbox. Was this not what you wanted to do?

To connect the desktop to the laptop you need to use eth0. So, I suggest that you try disconnecting the eth1 connection and try to get eth0 to connect. I am guessing that the GBit switch is in a convenient  location for using the laptop and is faster than going through Fritzbox. This is why you are trying to get things working this way.

Perhaps you need to come at this from another direction. Get the laptop to connect to the desktop. The desktop is always on. You do not want to physically go near the desktop. You want to share files, yes? Perhaps you should study Network Shares. Again, I do not have any experience of this. I am just trying to think of how I would try to set up what you are wanting to do. The things that I would examine. My post might encourage others more experienced to make comments.

Regards.

---

### Post by live4fun on 2010-11-11
Thanks for taking the time to look at my problem.

I am not currently looking at network shares as i am not yet able to get the connections straight. I intend to use ssh and ftp over ssh and see how it performs.

I guess the problem boils down to: 
How to configure two nics on one network.
Have the machine handle every internet related traffic through one nic and every local network related traffic through the other nic.
Major problem the network of both nics is the same.

I'll try to make the topic more clear about that.

Fallback perhaps to write a script to enable gigabit connection if switch is powerded (i am home everything up and running) and to use the 100mbit connection to my router only if the switch connection is not available.

I thought defining default route for the internet device would suffice for outgoing connections. While connecting to the ip of the gbit connection from my notebook would make sure traffic is handled on the gbit link.

Thanks to everybody taking the time to help :)

---

