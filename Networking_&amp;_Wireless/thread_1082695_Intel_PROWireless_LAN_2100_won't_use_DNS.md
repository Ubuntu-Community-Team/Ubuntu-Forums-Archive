---
title: "Intel PRO/Wireless LAN 2100 won't use DNS"
date: 2009-02-28
forum: Networking &amp; Wireless
---

### Post by porchrat on 2009-02-28
Hi all

I've installed Hardy Heron onto an old IBM Thinkpad (a T40) and I'm trying to get the wireless working.

It uses a Intel PRO/Wireless LAN 2100 mini PCI.  It associates with the router as I'm able to ping it and access the little interface that it comes with through Firefox. (although it completely ignores the settings in the GUI-based network manager - I had to set it up manually from the command line)

The problem is that while it connects to the router it doesn't use the router as a DNS and therefore has no internet access. The IP address of the router is present in /etc/resolv.conf as a nameserver:

```
nameserver XX-IP-address-of-router-XX
```

Is there another way to get this wireless module to set the IP address of the DNS.  I have already tried the GUI network manager and changing those settings has absolutely no effect on this thing whatsoever (although you can still change the IP address and netmask through it).

As an additional piece of info it connects to the router using a static IP.

---

### Post by porchrat on 2009-02-28
Seriously guys does someone have an answer for me?  I've searched around for an answer and can't find anything. Even if it just some command that needs to be run after every reboot I'll just create a script and run it when the laptop needs to be connected.

I'll take any suggestions.

---

### Post by porchrat on 2009-03-01
bump?

---

### Post by porchrat on 2009-03-02
bump (anyone?...please?)

---

### Post by netztier on 2009-03-02
> **porchrat said:**
> bump (anyone?...please?)

**Don't Panic! And stop bumping already!** :mad: 

Forums are not answer-my-question robots. If such were your attitude towards a forum, I suggest you rethink it.

Point is: you misphrased your topic considerably. 

WLAN cards have to clue about DNS and IP: they're Layer-2 devices and provide exactly that: transport of 802.11 frames. They have no clue and don't care about what these frames contain, be that IPv4, IPv6, NetBEUI, IPX or some other 802.2 stuff. DNS requests to them is just another bunch of bits.

Putting a DNS server's IP address in /etc/resolv.conf is *not* the WLAN NIC's (or any other NIC's) job, but it's up to team of NetworkManager, resolvconf and the installed DHCP client. 

You said you could ping your router's IP, so next thing is asking your DNS server manually:

```
user@host ~$ **dig @<yourDNSserversIP> www.google.com**
```

And see what happens. If that fails, try "dig"ging @ your ISP's DNS servers directly - you might find their IP addresses in your broadband router's web GUI.

regards

Marc

---

### Post by porchrat on 2009-03-02
Firstly let me apologise I didn't mean to come across as demanding an answer.  I've just been frustrated trying to figure it out. It is someone elses machine and I was hoping for an easy solution. My experiences with Linux have so far been very positive. This is of course not an excuse mind you so I do apologise for being a demanding ***.

I realise now that I haven't explained myself properly. It isn't the actual DNS I'm trying to connect to. I have two NAT devices (an internal wireless router that redirects to an external ADSL router) and I use the gateway IP (internal router) as the DNS address because it just translates out appropriately. I will try using the 'dig' command (wasn't aware of that one obviously) :).

I don't know if that is going to help though because, correct me if I'm wrong, but I already know the IP address and can clearly communicate with the router (I can ping it and change it's settings) wirelessly and therefore should be able to utilise that router address as a DNS.

Thank you for the reply I now have a direction and the explanation of wireless modules was very informative. I'm not in front of that machine at the moment, but the minute I get hold of it I will let you know how it went.

---

### Post by netztier on 2009-03-03
> **porchrat said:**
> but I already know the IP address and can clearly communicate with the router (I can ping it and change it's settings) wirelessly and therefore should be able to utilise that router address as a DNS.

Are you positive that this wireless router in question runs a "DNS proxy" and that it's actually a working one? There's routers out there that have just plain broken implementations of a DNS function, or ones that don't play nice with some resolvers (aka "DNS client"). OSX 10.5.6 users with a Fritz!Box xDSL router have stories to tell about such a case, and then some!

That's why I suggested accessing your ISPs DNS servers directly with **dig** (or it's older cousin **nslookup**), so that you bypass the router's possibly broken DNS proxy.


What you may have here might be even more of a troubleshooting nightmare:

The PC/Laptop you are on is talking to the DNS proxy on your wireless router. This is very probably because the DHCP service in that wireless router had given it's own IP address in "Option Domain Name Server" in the DHCP OFFER message - which is commonly done so.

Now - the DNS proxy on the wireless router itself needs to know about some "upstream" DNS server(s) itself - which it very probably learns by being a DHCP client on it's "WAN" interface. On that part of the network, the ADSL router most probably is the DHCP server, and it very probably will advertise itself as DNS-to-be-used as well.

So, that ADSL router very probably runs a DNS proxy of it's own, which in turn had learnt what your ISPs DNSs are via DHCP or PPPoE/PPPoA.

So you end up with a doubly cascaded DNS proxy setup - which might just be a bit difficult to troubleshoot - which of the DNS proxies is the problematic one?

**Suggestion:** find out the IP addresses of your ISP's DNS servers and configure the wireless router to use these instead of the DHCP-learnt one. As an alternative, check opendns.com, a free service for DNS servers to use.

regards

Marc

---

### Post by porchrat on 2009-03-06
> **netztier said:**
> Are you positive that this wireless router in question runs a "DNS proxy" and that it's actually a working one? There's routers out there that have just plain broken implementations of a DNS function, or ones that don't play nice with some resolvers (aka "DNS client"). OSX 10.5.6 users with a Fritz!Box xDSL router have stories to tell about such a case, and then some!

That's why I suggested accessing your ISPs DNS servers directly with **dig** (or it's older cousin **nslookup**), so that you bypass the router's possibly broken DNS proxy.


What you may have here might be even more of a troubleshooting nightmare:

The PC/Laptop you are on is talking to the DNS proxy on your wireless router. This is very probably because the DHCP service in that wireless router had given it's own IP address in "Option Domain Name Server" in the DHCP OFFER message - which is commonly done so.

Now - the DNS proxy on the wireless router itself needs to know about some "upstream" DNS server(s) itself - which it very probably learns by being a DHCP client on it's "WAN" interface. On that part of the network, the ADSL router most probably is the DHCP server, and it very probably will advertise itself as DNS-to-be-used as well.

So, that ADSL router very probably runs a DNS proxy of it's own, which in turn had learnt what your ISPs DNSs are via DHCP or PPPoE/PPPoA.

So you end up with a doubly cascaded DNS proxy setup - which might just be a bit difficult to troubleshoot - which of the DNS proxies is the problematic one?

**Suggestion:** find out the IP addresses of your ISP's DNS servers and configure the wireless router to use these instead of the DHCP-learnt one. As an alternative, check opendns.com, a free service for DNS servers to use.

regards

Marc

Sorry it took me so long to get this machine back. :(

You are 100% correct about my network setup. However I know for certain that it is working as there are 5 other machines on this network all working flawlessly using (as far as they are concerned) that internal router as the DNS. There is definitely no troubleshooting of the network infrastructure required.

There are both wired and wireless machines on this network. Running a variety of operating systems and the wireless module in this particular machine isn't faulty because this machine ran XP a week ago and wireless was not an issue.

Unless I misunderstood what you were saying, which is possible.

---

### Post by porchrat on 2009-03-07
OK I've managed to track down a promising looking driver.

I seems like it is a community project started by Intel to provide Linux drivers for the PRO/Wireless LAN 2100.

Feel free to take a look at it [here]("http://ipw2100.sourceforge.net/")

Problem is I need to do a few checks before I can build and install this thing (if it is even possible to build this thing on Ubuntu).

I have downloaded the driver and the firmware, but I need to remove or blacklist the driver that isn't working (the one Ubuntu came with and is using currently). The first problem is this: Is there a way to discover which driver is being used by Ubuntu? Some sort of command that will do that?

---

