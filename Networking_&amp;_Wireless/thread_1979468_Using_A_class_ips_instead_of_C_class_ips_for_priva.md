---
title: "Using A class ips instead of C class ips for private network"
date: 2012-05-13
forum: Networking &amp; Wireless
---

### Post by absoord on 2012-05-13
Hi all!

Just a question, maybe it seems obvious for many of you but I've been trying to find some info on the net and just found definitions...

When I install any system at home it automatically gets a C class IP (192.168.0.x). It's ok if I have 254 devices on my local network but what if I need 500 devices? I guess I would start using B or even A classes private IPs, but the question is: What would I need to reconfigure my network using 10.x form IPs? Any installation of ubuntu I get a C class IP, so the question is how to do to acquire automatically an A class IP?

Does it have something to do with the router capability to distribute this class of IPs?

Thanx so much!

---

### Post by mamut0o1 on 2012-05-13
It depends on the routers capabilities, if the router is capable then you can subnet that IP to 192.168.0.1/23 instead of 192.168.0.1/24 as you currently have. if you subnet that IP as I mentioned above then you will have 510 available hosts in your network. 
=)

---

### Post by SeijiSensei on 2012-05-13
Either use a [designated]("http://www.faqs.org/rfcs/rfc1918.html") class-B private address block or a class A.  For class-B use something like 172.16.0.0/16.  That gives you 65K addresses.

> Any installation of ubuntu I get a C class IP, so the question is how to do to acquire automatically an A class IP?

There's nothing about Ubuntu, or Linux, that limits your address space.  If you use DHCP, then configure the DHCP server to hand out addresses in the range you desire.  If you use static addressing, then just make sure you have the right IP and subnet mask in the definitions.  I've used Linux boxes as a router for class A, B, and C networks.

---

### Post by absoord on 2012-05-14
> **SeijiSensei said:**
> Either use a [designated]("http://www.faqs.org/rfcs/rfc1918.html") class-B private address block or a class A.  For class-B use something like 172.16.0.0/16.  That gives you 65K addresses.



There's nothing about Ubuntu, or Linux, that limits your address space.  If you use DHCP, then configure the DHCP server to hand out addresses in the range you desire.  If you use static addressing, then just make sure you have the right IP and subnet mask in the definitions.  I've used Linux boxes as a router for class A, B, and C networks.

Ok, suppose I want to build a DHCP server handling class-A ips. How would I configure the desktop devices to ask for a DHCP ip from the server instead of the router?

Thanx guys for the responses!

---

### Post by Lars Noodén on 2012-05-14
Why not just configure the router's DHCP server to deliver the address range you want?  It should be running either ISC dhcpd or Dnsmasq.  Either one is configurable that way.  Which model is it?

---

### Post by absoord on 2012-05-14
I'm using a pretty old one :) Scientific Atlanta 2320

I'm not sure it's possible to do configure it that way, but I would still like to configure it through a DHCP server, just to learn how these things work. I'm not sure how to set it up to get DHCP IPs from the server and not from the router. Is it strictly necessary a topology like this...?

Desktop devices -> switch -> dhcp server -> router

Or is there any configuration to make it work that way even if the dhcp server is 'before' the switch?

Thanx!!

---

### Post by Lars Noodén on 2012-05-14
A better set up, if possible, would be :

Desktop devices -> switch -> router

That is because the router already has a DHCP server and it would be best to use that if possible.  Take a look at the router's settings and see if it is possible to configure it to serve the address range you want.  If found some documentation for the Scientific Atlanta 2320, and it looks like the address range might be hardcoded.

To replace it, you will have to either turn off its DHCP capability or block it on the network.  From my limited understanding of the protocol, it does not work to have two competing DHCP servers on the same LAN.  

You will be using one of the following to set up your replacement:

[http://manpages.ubuntu.com/manpages/precise/en/man8/dnsmasq.8.html](http://manpages.ubuntu.com/manpages/precise/en/man8/dnsmasq.8.html)
[http://manpages.ubuntu.com/manpages/precise/en/man8/dhcpd.8.html](http://manpages.ubuntu.com/manpages/precise/en/man8/dhcpd.8.html)

---

### Post by hawkmage on 2012-05-14
Back in 1993 the strict requirement for Class A/B/C addressing was gotten rid of by using CDIR (Classless Inter-Domain Routing)  You can use any part or all of the 192.168.0.0/16 or 172.16.0.0/12 or even the 10.0.0.0/8 private IPv4 address spaces.

There is no reason that you can't supernet  any adjacent /24 portions of the private 192.168.0.0/16 address space (This is what mamut0o1 was referring to  above).   Or you can subnet the 172.16.0.0/12 or 10.0.0.0/8 address spaces.  

What you can do with your network really depends on what your networking equipment will support.  Linux or any modern networked OS should be able to handle any of these solutions.

---

### Post by SeijiSensei on 2012-05-14
If you have a server on the network running Linux, then I would disable the DHCP server in your router and run dhcpd on the Linux server.  You can configure dhcpd.conf to serve up pretty much any subnet you want if you can calculate the right mask.  As mamut0o1 says, you could use 192.168.0.0/23 and get 510 hosts (= 2^(32-23) - 2; the network address and the broadcast address cannot be assigned to hosts.) Using /22 gives you 1022 hosts.

You can use any RFC1918 prefix in these assignments.  For instance 10.0.0.0/23 also has 510 addresses.  You can generate a "class-B" from 10.0.0.0 by using the /16 mask.  10.1.0.0/16 is the CIDR address that would number 65,534 hosts from 10.1.0.1 through 10.1.255.254.

If you are not stuck with the Scientific Atlanta, I'd buy a new router that you can flash with [dd-wrt](http://www.dd-wrt.com/site/index) or [tomato](http://www.polarcloud.com/tomato), especially if you need to support wifi. Another option is to build your own router with Linux.  It's easiest if you use two Ethernet cards, one that points to the Internet and the other connected to the LAN.  You'd run dhcpd on the box (bound to the internal interface) and iptables to masquerade traffic to and from  the Internet.  I proxy port 80 requests through Squid on routers as well to generate detailed logs of browsing by IP address.  To offer wifi you'd need to connect an Access Point bridged to the Linux router.

---

### Post by absoord on 2012-05-16
Ok, thank you guys for the info :-)

---

