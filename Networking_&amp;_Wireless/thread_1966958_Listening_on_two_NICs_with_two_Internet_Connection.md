---
title: "Listening on two NICs with two Internet Connections"
date: 2012-04-27
forum: Networking &amp; Wireless
---

### Post by cheracc on 2012-04-27
I have spent days researching how to make this work and I'm at the end of my rope. I would love some assistance, as I feel this should be easy, and I'm frustrated that its proving to be otherwise.

I'm by no means a networking guru but I will try my best to coherently explain what I have going on.

I am running Ubuntu Server 11.10 on a machine with 2 NICs (eth0 and eth1). I also have two separate internet connections and a local network. I am running apache2 and would like to be able to reach the same web directory externally from either interface.

eth0 is connected to my router with a static IP (192.168.13.120) and the router is configured with a DMZ to this machine. The router receives its IP address through dhcp (I will call this address IP0).

eth1 is connected directly to a cable modem, and receives its IP address through dhcp (I'll call this one IP1)

I would like to be able to reach my apache server using either of these external IP addresses.

I've tried all kinds of stuff with /etc/network/interfaces, and I can always get one of these addresses to reach my web server, but not both. It appears that whichever interface gets loaded first is the one that ends up being reachable. The other simply times out. 

Apache is set up basically with default settings, to listen on *:80

My original /etc/network/interfaces looks like this:
```

auto lo
iface lo inet loopback

auto eth0 eth1
iface eth1 inet dhcp

iface eth0 inet static
address 192.168.13.120
netmask 255.255.255.0

```This allows me to reach my webserver using IP1 (since it's loaded first apparently) but not IP0. If I simply re-order this with the "iface eth0 inet static" section first, then I can reach the web server using IP0 but not IP1. In either case, I can always reach it using the local address of 192.168.13.120.

I have tried bridging them with something like this (again, I couldn't find a scenario out there that matches exactly what I have going on, so this could be completely wrong) I've tried both with and without those commented lines and neither works.

```

auto eth0
iface eth0 inet static
address 192.168.13.120
netmask 255.255.255.0

auto eth1
iface eth1 inet manual

auto br0
iface br0 inet dhcp
bridge_ports eth1 eth0
#bridge_stp off
#bridge_fd 0
#bridge_maxwait 0

```This again allows me to connect through IP1 (eth1) but not IP0

If it matters, here is my ifconfig output (with the above interfaces configuration):

```

br0       Link encap:Ethernet  HWaddr 00:1d:**
          inet addr: **IP1**  Bcast:255.255.255.255  Mask:255.255.254.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:179244 errors:0 dropped:0 overruns:0 frame:0
          TX packets:95571 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:9869744 (9.8 MB)  TX bytes:58415461 (58.4 MB)

eth0      Link encap:Ethernet  HWaddr 00:1d:**
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17532 errors:0 dropped:0 overruns:0 frame:0
          TX packets:141112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1970345 (1.9 MB)  TX bytes:11296740 (11.2 MB)
          Interrupt:41 Base address:0xa000

eth1      Link encap:Ethernet  HWaddr 00:1d:**
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:896731 errors:1 dropped:0 overruns:0 frame:1
          TX packets:367993 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:62474671 (62.4 MB)  TX bytes:325127447 (325.1 MB)
          Interrupt:42 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:275 errors:0 dropped:0 overruns:0 frame:0
          TX packets:275 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:22486 (22.4 KB)  TX bytes:22486 (22.4 KB)

```Please tell me I'm making this too hard?

---

### Post by SeijiSensei on 2012-04-27
I believe you want to use the "[bonding]("http://www.linuxfoundation.org/collaborate/workgroups/networking/bonding")" driver.  I've been thinking about this to bond together two wifi connections to separate routers to improve my speeds.  My external connection is something like 30 Mbit, and I don't come close to that over one wifi adapter because 802.11 uses "half duplex" connections.

---

### Post by cheracc on 2012-04-27
Thanks for your insight, that link was way over my head, but googling "bonding" has led me to some promising leads. I'll try some of this in the morning and see if I can't make something stick.

---

### Post by HermanAB on 2012-04-28
Howdy,

Read the Advanced Networking Howto at The Linux Documentation Project tldp.org.  What you want to do is described in there.

---

### Post by cheracc on 2012-04-28
Thank you!

I found exactly what I needed right here: [http://tldp.org/HOWTO/Adv-Routing-HOWTO/lartc.rpdb.multiple-links.html](http://tldp.org/HOWTO/Adv-Routing-HOWTO/lartc.rpdb.multiple-links.html)

---

