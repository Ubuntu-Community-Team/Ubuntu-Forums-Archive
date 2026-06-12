---
title: "Magical IPv6 Address?"
date: 2010-01-30
forum: Networking &amp; Wireless
---

### Post by WinstonChurchill on 2010-01-30
When I run 'ifconfig', Linux tells me I have an IPv6 address on the internet. I don't think this can be right because:

[LIST=1]
[*]I am quite certain that the cable modem only supports DOCSIS v2, which I thought didn't support IPv6
[*]I can't seem to do anything IPv6-related (ping, visit ipv6.google.com, etc), although I may not be going about this the right way
[*]My ISP is RoadRunner, and they don't seem to be able to do anything very well at all - I have a hard time believing they're serving customers IPv6 addresses.
[/LIST]
So... is there another explanation for this? And if this is a legit IPv6 address, what do I need to do to make it work?

(eth0 is my internal network, and eth1 is the internet interface. This server does NAT for my LAN)
```

root@Server:/# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:d1:1a:19:f4
          inet addr:10.0.0.1  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:d1ff:fe1a:19f4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1586024 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3087226 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:138292300 (138.2 MB)  TX bytes:61250465 (61.2 MB)
          Interrupt:21 Base address:0xcc00

eth1      Link encap:Ethernet  HWaddr 00:11:95:36:58:00
          inet addr:76.184.XXX.XXX  Bcast:255.255.255.255  Mask:255.255.240.0
          inet6 addr: fe80::211:95ff:fe36:5800/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15589063 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2771395 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2688697974 (2.6 GB)  TX bytes:743812070 (743.8 MB)
          Interrupt:22 Base address:0x800
```

---

### Post by nacnud1 on 2010-01-30
That's what is called a "link-local" IPv6 address.  Your machine will automatically configure it.  It mean you are IPv6 capable, but do not have global access.  Here's an easy way to get global access:

sudo apt-get install miredo
sudo vim /etc/default/miredo  

**change the "#START_MIREDO=true" to "START_MIREDO=true"

then start it:

sudo /etc/init.d/miredo start

and you will be cooking with IPv6 gas!

---

### Post by nacnud1 on 2010-01-30
or if you are running as a server and you want the server to be your IPv6 router for all the PCs in your network use GoGoNet/Freenet6:

sudo apt-get install gw6c

then vi ino the gw6c.conf file and change it to being a router..

then make sure you allow IPv6 forwarding in "/etc/sysctl.conf"

uncomment this "#net.ipv6.conf.all.forwarding=1"

restart the network then:
/usr/local/gw6c/bin/gw6c -f /usr/local/gw6c/bin/gw6c.conf

---

### Post by WinstonChurchill on 2010-01-30
> **nacnud1 said:**
> or if you are running as a server and you want the server to be your IPv6 router for all the PCs in your network use GoGoNet/Freenet6:

sudo apt-get install gw6c

then vi ino the gw6c.conf file and change it to being a router..

then make sure you allow IPv6 forwarding in "/etc/sysctl.conf"

uncomment this "#net.ipv6.conf.all.forwarding=1"

restart the network then:
/usr/local/gw6c/bin/gw6c -f /usr/local/gw6c/bin/gw6c.conf

Thanks for the help - I do have a few more questions though: if I'm routing IPv6 for the PC's in my network, is it doing Network Address Translation, or will each PC have a globally addressable IPv6 address? And do I tell my dhcpd to assign these, or will the PC's get them over the tunnel? What about DNS servers? And finally, what is the bandwidth like through this IPv6 tunnel? It seems hard to believe they would be able to provide you with much since it's free...

---

### Post by nacnud1 on 2010-01-31
> **WinstonChurchill said:**
> Thanks for the help - I do have a few more questions though: if I'm routing IPv6 for the PC's in my network, is it doing Network Address Translation, or will each PC have a globally addressable IPv6 address? And do I tell my dhcpd to assign these, or will the PC's get them over the tunnel? What about DNS servers? And finally, what is the bandwidth like through this IPv6 tunnel? It seems hard to believe they would be able to provide you with much since it's free...

1. No, the IPv6 router will function as a router issuing Router Advertisements (RA) witch give each host a globally routable IPv6 address.  For example, my webserver is this: [http://[2001:5c0:1100:6400::1]/](http://[2001:5c0:1100:6400::1]/)

2. No need for DHCP, you have what's called Stateless Address Autoconfiguation: [http://en.wikipedia.org/wiki/IPv6#Stateless_address_autoconfiguration](http://en.wikipedia.org/wiki/IPv6#Stateless_address_autoconfiguration)

3. Believe it or not, bandwidth is better!  Not as many hops and no translation like in IPv4...

---

### Post by WinstonChurchill on 2010-01-31
> **nacnud1 said:**
> 1. No, the IPv6 router will function as a router issuing Router Advertisements (RA) witch give each host a globally routable IPv6 address.  For example, my webserver is this: [http://](http://)[2001:5c0:1100:6400::1]/

2. No need for DHCP, you have what's called Stateless Address Autoconfiguation: [http://en.wikipedia.org/wiki/IPv6#Stateless_address_autoconfiguration](http://en.wikipedia.org/wiki/IPv6#Stateless_address_autoconfiguration)

3. Believe it or not, bandwidth is better!  Not as many hops and no translation like in IPv4...

Thanks!

---

