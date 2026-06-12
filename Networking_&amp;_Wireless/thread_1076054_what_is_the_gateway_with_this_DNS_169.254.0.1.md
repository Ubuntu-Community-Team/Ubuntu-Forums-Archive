---
title: "what is the gateway with this DNS 169.254.0.1"
date: 2009-02-20
forum: Networking &amp; Wireless
---

### Post by powel212 on 2009-02-20
what is the gateway with this DNS 169.254.0.1

if

DNS 168.254.0.1
netmask 255.255.0.0

then what is
address range: ?.?.?.? to ?.?.?.?
gateway ?.?.?.?

Thanks

I am still new to networking but slowly getting better.

attached is a diagram of my setup

---

### Post by superprash2003 on 2009-02-21
dont set both ubuntu and windows with same ip 192.168.0.1?? are you setting a local DNS server??you dont need one!!you just need your ISP given DNS servers or opendns servers for internet access.

---

### Post by powel212 on 2009-02-21
I realized too late that my graphic is missing the routers. Rather key. 

Both the Ubuntu and windows boxes have separate routers. so both can happily run 192.168.0.1 on subnet 255.255.255.0

each box has 2 nework cards so lets call them card 1 and card 2

each box's card one runs a line to the internet using 192.168.0.1 this is designed to have them doth running DHCP to the internet. It actually works great. and they can not see each other and are not aware of each other on 192.168.0.1 as is the design.

On card 2 of each machine i run a direct link between the 2 computers via a switch. here I have to use 168.254.0.1 so the computers don't get confused. But I don't know the address range of 169.254.0.1 so I am using DHCP but I want to change to manual settings.

I am hoping someone has used 169.254.0.1 before and can tell me the address range and default gateway.

Thanks

---

### Post by capscrew on 2009-02-21
> what is the gateway with this DNS 169.254.0.1
As you ask the question; the gateway is the nearside address of the local router for the network.  

In this case it would be the other NIC's address (ie: 192.168.0.1). As you have a "multi-homed host" It can be considered a router (layer 3/4). Think of the implications of having 4 routers and 2 gateways that are the same (e.g. 192.168.0.1) in this network! 

If you insist; why use 168.254.n.n at all?  If you are only looking for a separate private network, you can use any 192.168.x.0/24 other than the 192.168.0.0/24.

Let's say you use 192.168.**100**.0/24 as the network.  You could then use 192.168.**100**.1 and 192.168.**100**.2 as the IP addresses.

This is all theory.  I wouldn't do any of this at all.  What are you trying to accomplish with this?  Are you just experimenting?

---

### Post by powel212 on 2009-02-22
Hey

Great answer. Thanks. 

I did not know you could have one Network card running 192.168.0.1 and another at 192.168.100.0/24 - I was only using the 169.254.0.1 because it's the only other configuration I thus far knew of.

I am certainly experimenting and fooling around. Learning as I go.

My problem I fixed with a really big hammer - a new $100.00 router. haha

My original goal was to use my existing, (older), equipment to create on the one hand two completely separate internet connections and on the other hand to create a direct link between the 2 machines through separate network cards so that I could transfer large files through the "Direct Link" without blasting too much traffic through my existing routers.

The file server is an old intel P1 733Mhz i built from spare part. It is easy on power so it runs all the time which allows me to shut down my desktop box which is truly a power hog.

See attached graphic for my current working configuration.

Best throughput on original configuration 6.5M/s
Best throughput on current configuration 7.9m/s

---

### Post by capscrew on 2009-02-22
Glad that worked out for you.  To further clarify what the /24 means -- The first 24 bits of the address (in this case the first 3 octets (192.168.N) are the network and the last 8 bits (octet) are the network IP addresses.  This means we have 254 legit IP addresses (1-254).  There are also 256 networks (0-255) in the 192.168.N.x/24 range.  So we are not restricted to just one network in this range.

This is how my system is configured.  The local traffic between the the 2 hosts you show does not transit the router at all.  It all is handled by the switch.  Only WAN traffic (internet) transits the router.

---

### Post by powel212 on 2009-02-22
Thanks again.

I will try some more configurations just for its own sake. Thanks for the fuel for my fire.

Powel

---

### Post by powel212 on 2009-02-22
Quick question.

Do you know any online resources where I can learn more about multi-homed host?

Most of the stuff I have found on my own is either over my head or in many cases cryptic and seemingly incomplete.

Thanks

Powel

---

### Post by capscrew on 2009-02-22
What is it that you want to know?  The term multi-homed host generally refers to any host that has multiple network interfaces.  The only reason I can think of to have this is to connect multiple networks together at the layer 3/4 level. As you have done with your router (local to internet).  Cisco routers are multi-homed hosts. 

The same hardware can also be used for bridging (layer 2) Ethernet connections.  This would either be as a switch or a bridge.  Your new switch is in this category along Cisco Catalyst managed switches. 

I would look for information on "Linux routers" or "Linux bridging".  In addition you can read up on "switched networks".

Edit:  This is all you need to configure routing in Linux (Ubuntu style)
[http://documents.made-it.com/Debian_Internet_Server/Debian_Internet_Server-13.html]("http://documents.made-it.com/Debian_Internet_Server/Debian_Internet_Server-13.html")

A typical router is nothing more than the above plus extras like DHCP and a firewall.

Edit2: Here is some info on bridging.
[http://www.linuxfoundation.org/en/Net:Bridge]("http://www.linuxfoundation.org/en/Net:Bridge")
I would never use a Linux multi-homed host as switch. The cost per port is to much.  Figure how much you paid for your switch and divide by the number of ports.  Pretty cheap for an unmanaged switch.   A managed switch is a different animal and that still is cheaper to buy than to build and configure.  Maybe I would  bridge two interfaces in unique situations. 

If this does not answer your questions, feel free to ask some more.

---

### Post by powel212 on 2009-02-24
Best throughput as of feb 25/09 = 10.17m/s

Faster than my stupid pocket flash drive. haha. (still don't know why people think flash is fast).

---

