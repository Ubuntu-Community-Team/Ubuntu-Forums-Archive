---
title: "NIC Bonding/Teaming and Switches"
date: 2011-06-20
forum: Networking &amp; Wireless
---

### Post by spynappels on 2011-06-20
Hi guys,

I have a question about bonded NICs and the switches they are connected to. If I am wrong in any of my assumptions, please correct me.

I have a server which needs to send a lot of data to another server quickly. Both have multiple GbE NICs. I understand what is required at the server end (I think) in that a pseudo-interface is created such as bond0 with the IP applied to that interface rather than eth0 and eth1.

My question relates to the connection between the servers, i.e. the switch. Is a specific type of switch required for this to work, as an IP will have 2 (or more) MAC addresses associated with it, or how does the switch decide to which port to route the traffic for the bond0 IP?

Also, will this only work when multiple connections are being made? What I mean is, will each individual TCP connection only use either the physical eth0 OR the physical eth1 interface, or can a single connection make use of the aggregated bandwidth, sending one packet to one physical interface and another to the other physical interface, using the bond0 IP as the destination?

What I am trying to work out is if I had a storage server connected to an application server and exporting storage using NFS or GlusterFS, would an aggregated link improve throughput?

---

### Post by dapperdanny77 on 2011-06-20
maybe this is a starting point for you

[https://secure.wikimedia.org/wikipedia/en/wiki/Link_aggregation](https://secure.wikimedia.org/wikipedia/en/wiki/Link_aggregation)


your network device(s) has to  support bonding

---

### Post by spynappels on 2011-06-20
Thanks, I had read that page, and I've re-read it again, might need a few more passes to find what I'm looking for......


> **dapperdanny77 said:**
> 
your network device(s) has to  support bonding

I guess you are referring to switches here? 

Off to do more reading then.

---

### Post by dapperdanny77 on 2011-06-20
> I guess you are referring to switches here? 

yes - cisco for instance delivers switches supporting LACP - i'm quite sure cisco provides related information also

... saw this working on nortel devices too

---

### Post by spynappels on 2011-06-20
Cool, I've been looking at some Netgear Smart switches for a test environment, can't afford Cisco stuff. I think I'm getting the idea though, thanks.

---

### Post by bab1 on 2011-06-20
> **spynappels said:**
> Cool, I've been looking at some Netgear Smart switches for a test environment, can't afford Cisco stuff. I think I'm getting the idea though, thanks.

See [**_[COLOR="Blue"]here[/COLOR]_**]("http://www.cainetworks.com/support/training/setup-link-aggregation-netgear.html") for a Netgear setup.


Quoting from another article: *"Link Aggregation is also referred to as Port Trunking, Port Teaming, Ethernet Trunking, and Link Bundling.  Cisco has a a multi-port proprietary technology known as EtherChannel.  All refer to the same concept; multiple ports acting as a single connection between network devices.  The key to setting up Link Aggregation between different brands is ensuring they both support the **IEEE standard 802.3ad**."*

The full article is [**_[COLOR="Blue"]here[/COLOR]_**]("http://www.smallnetbuilder.com/content/view/30556/53/")

---

### Post by doas777 on 2011-06-20
> **spynappels said:**
> Cool, I've been looking at some Netgear Smart switches for a test environment, can't afford Cisco stuff. I think I'm getting the idea though, thanks.
I have a netgear smart switch and it does support Link Aggregation, but looking at the manual I can't tell if mine is a 802.1ax or 802.3ad.

---

### Post by spynappels on 2011-06-21
Thanks for that guys. I've been looking at the GS108T and it says that it supports 802.3ad, but I guess I'll need to check that it supports LACP, I've seen posts where it will only allow the static setting and that LACP is not supported even though it says 802.3ad compliant.

Thanks for all the pointers.

---

