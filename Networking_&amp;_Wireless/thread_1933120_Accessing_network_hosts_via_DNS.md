---
title: "Accessing network hosts via DNS"
date: 2012-02-28
forum: Networking &amp; Wireless
---

### Post by WARlrus on 2012-02-28
Hi,

Please forgive me if this is a stupid question, or in the wrong place!

I have a number of hosts on my local network, performing a variety of tasks on a variety of ports, and I want to be able to pick them out individually from outside my network using some combination of DNS/IPTables/DCHP/Whatever else.

So - here's the scenario if that wasn't clear. I have two machines, blue and green, that both run SSH on port 22. I (hypothetically) own the domain example.com, and want 'ssh blue.example.com' to do the right thing, and point me at SSHD running on blue. This is easy enough to do internally, but I want to be able to do this from anywhere...

Adding the local address to DNS (BIND9 on one machine within the network) doesn't work externally (obviously... now I've tried it) as the machine I'm accessing the domain from tries to look up the 192.168.0.X address on it's own network, not mine.

Any help or pointers in the right direction would be very much appreciated :-)

---

### Post by WARlrus on 2012-02-29
I'm beginning to think I need some sort of iptables rule that depends on the source of the request - can anyone point me in the right direction?

---

### Post by dandnsmith on 2012-02-29
I think that it isn't good enough to hypothetically own a domain - you need, if you want to be able to access the sorts of services you've hinted from outside, to register your own domain. You then need to either build your own DNS support, or to host the domain with an external 'authority' in such a way that you can address the required elements of the domain externally.

I'm sorry, that all looks a bit turgid and incomprehensible, but you're on the edge of 'real' networking - a significant step on from just internetting via an ISP who provides all the access.

---

### Post by WARlrus on 2012-02-29
Hi,

Sorry, I probably wasn't clear in the original post - I do own a domain I want pointing at my services, just wasn't keen to broadcast it here :-)

For the sake of clarity - I own a domain similar to warlrushouse.net (so let's use that for examples!) and want to be able to use blue.warlrushouse.net and green.warlrushouse.net as domain names to access the servers behind my single connection individually. I can't do this with an external provider, as blue and green sit behind a single IP.

I am running a DNS server on blue, but don't know how to configure that properly. At the moment, the db.warlrushouse.net file looks like:

```

;
; BIND data file for warlrushouse.net
;
$TTL    604800
@       IN      SOA     ns.warlrushouse.net. root.warlrushouse.net. (
                      201202281         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.warlrushouse.net.
ns      IN      A       192.168.0.5
blue    IN      A       192.168.0.5
green   IN      A       192.168.0.4

```

But obviously, that's daft, as anything outside my internal network doesn't know what 192.168.0.5 actually is.

I'm aware I'm getting into the deep dark areas of 'real' networking - that's exactly where I want to go, to learn about this stuff!

---

### Post by bab1 on 2012-02-29
> **WARlrus said:**
> Hi,

Sorry, I probably wasn't clear in the original post - I do own a domain I want pointing at my services, just wasn't keen to broadcast it here :-)

For the sake of clarity - I own a domain similar to warlrushouse.net (so let's use that for examples!) and want to be able to use blue.warlrushouse.net and green.warlrushouse.net as domain names to access the servers behind my single connection individually. I can't do this with an external provider, as blue and green sit behind a single IP.

I am running a DNS server on blue, but don't know how to configure that properly. At the moment, the db.warlrushouse.net file looks like:

```

;
; BIND data file for warlrushouse.net
;
$TTL    604800
@       IN      SOA     ns.warlrushouse.net. root.warlrushouse.net. (
                      201202281         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.warlrushouse.net.
ns      IN      A       192.168.0.5
blue    IN      A       192.168.0.5
green   IN      A       192.168.0.4

```

But obviously, that's daft, as anything outside my internal network doesn't know what 192.168.0.5 actually is.

I'm aware I'm getting into the deep dark areas of 'real' networking - that's exactly where I want to go, to learn about this stuff!

I think you should break the problem down even further.  There are 3 parts to your question: 1. Domain Names 2. LAN/WAN (IPTables/NAT) 3. DHCP.  These are all part of TCP/IP (the IP stack).  Here are a few examples to think about.  

The domain name as the as the family name of all the hosts (computers) in you network.  let's will use the [COLOR="Red"]domain name[/COLOR] of *trees.com*.  Each host has a name ([COLOR="Blue"]hostname[/COLOR]) such as *oak or pine or maple* (like you a or b).  A FQDN (fully qualified domain name) would be [COLOR="Blue"]pine[/COLOR].[COLOR="Red"]trees.com[/COLOR].

DNS resolves FQDN to IP addresses.  You need to provide this resolution on the public side (Internet) as well as internally (private addresses i.e 192.168.n.n).  

There is a separation between the LAN and the Internet (your router) and this is where the public IP provided by your ISP is mapped to you private network IP.  This is NAT (Network Address Translation.  A Linux host with 2 NIC's and IPTables provides NAT and packet forwarding.

DHCP is for centralizing network IP address assignment.  This needs to be coordinated with DNS as the IP address will be mapped to the hostname.

You can see how this all is interrelated,but with separate protocols.  Hope it helps.  I'm sure it will raise new questions

---

### Post by dandnsmith on 2012-02-29
When I talked about registering a domain, I was referring to more than just the domain name.
It has been a good while since I did it, but then I requested a block of IP addresses to be associated with the domain - and this is what gives the resource to allow external access to different resources.
I'd be interested to hear if you can do it a different way (excluding the obtaining of the externally usable addresses from an ISP, which I regard as equivalent).

---

### Post by bab1 on 2012-02-29
> **dandnsmith said:**
> When I talked about registering a domain, I was referring to more than just the domain name.
It has been a good while since I did it, but then I requested a block of IP addresses to be associated with the domain - and this is what gives the resource to allow external access to different resources.
I'd be interested to hear if you can do it a different way (excluding the obtaining of the externally usable addresses from an ISP, which I regard as equivalent).
To *own *an Internet Domain is to register it.

I try an think of this as```

1. Provision the block of IP addresses = ISP provides the addresses.  If this is to a
   physical location, the drop is to the emarcation  point ([**_[COLOR="Blue"]demarc[/COLOR]_**]("http://en.wikipedia.org/wiki/Demarcation_point")) and you are
   limited to the ISP in your area.  This can be any ISP that has access to you 
   (i.e. telco or cable).  This could include wireless broadband in the future 
   (it's still the telco).   
    
2. Provision domain name = usually through a [**_[COLOR="Blue"]DNS registrar[/COLOR]_**]("http://en.wikipedia.org/wiki/Domain_name_registrar")

3. Arrange for [**_[COLOR="Blue"]DNS hosting[/COLOR]_**]("http://en.wikipedia.org/wiki/DNS_hosting_service") = This is to point the domain name to the block of 
   IP addresses you control.  This is usually handled by the registrar. 
```

By breaking this into 3 distinct areas of concern you have flexibility.  Sometimes folks change ISP's and find that they don't own the domain name (the ISP does and wont allow you to take it with you).  What happens If you decide to host the domain through a VPS or co-location site?  You will be assigned IP addresses from the VPS or Co-Lo.  It is simple to change the DNS when you control it.

Most large companies will just get the block of IP addresses and register the domain name.  They provide their own DNS hosting, both internally (LAN) and publicly (WAN).

This is a very simple version of what can be done.  Of course you could still just use the ISP to provide all of this, but at least would know what can happen if you do; and that it can be split up.

---

### Post by dandnsmith on 2012-03-01
A further note, as I haven't made it clear.
It doesn't have to be the ISP which gets the IP addresses - the case I was talking about of some years ago the addresses were allocated by the appropriate registration authority. All the arrangement of DNS and IP addresses were then carried out within my company (no ISP involved).

At present it would be difficult to get a block of IP4 addresses as they are in such short supply.

---

### Post by bab1 on 2012-03-01
> **dandnsmith said:**
> A further note, as I haven't made it clear.
It doesn't have to be the ISP which gets the IP addresses - the case I was talking about of some years ago the addresses were allocated by the appropriate registration authority. All the arrangement of DNS and IP addresses were then carried out within my company (no ISP involved).

At present it would be difficult to get a block of IP4 addresses as they are in such short supply.

All the IPv4 addresses have been allocated to specific authorities.  I don't believe you can directly purchase a block of IPv6 addresses.

It is true that originally companies could purchase a block of IP addresses.  For example, General Electric owns 3.0.0.0 and IBM owns 9.0.0.0.

---

### Post by dandnsmith on 2012-03-02
OK, so we're in agreement, essentially, about how it works.
The thing WARlrus has to sort out is the interfacing to his network, and the allocation of real addresses to his services/machines (not non-routable addresses in the 192.168.x.y or any of the other 'private' ranges).

---

### Post by bab1 on 2012-03-02
> **dandnsmith said:**
> OK, so we're in agreement, essentially, about how it works.
The thing WARlrus has to sort out is the interfacing to his network, and the allocation of real addresses to his services/machines (not non-routable addresses in the 192.168.x.y or any of the other 'private' ranges).
Indeed, @WARlrus will most likely be at a remote host (computer) and will have to traverse the Internet to reach his host(s) which will be behind NAT (private addressing) also on his LAN.  So he will have the the added complexity of the NAT to deal with.

Back when companies could buy whole blocks of IP addresses all hosts directly faced the public internet.  Common practice today is to control 1 pubic address and NAT multiple hosts on the LAN.  

The NAT can handle the multiple LAN addresses to 1 public address relationship.  When you are running servers (web, etc.) and NAT is employed, you have to "port forward" the traffic to a specific host.  For example if you had a web server behind NAT then all traffic on TCP port 80 would have to be forwarded to the web server.  

One limitation of employing NAT is that only one host can use TCP port 80 in this scheme.  If you had 2 web servers then 1 of those would have to use a different TCP port.

If @WARlrus is going to use Linux as the router OS then IPtables will provide the Routing/NAT/Firewall functionality.  As this machine would be at the *edge *of his network (the gateway) so DHCP and DNS (local only) services could be provided too.

---

### Post by WARlrus on 2012-03-03
> **bab1 said:**
> Indeed, @WARlrus will most likely be at a remote host (computer) and will have to traverse the Internet to reach his host(s) which will be behind NAT (private addressing) also on his LAN. 


That is pretty much exactly what I'm after here - it's becoming fairly obvious that having box1.mydomain.net and box2.mydomain.net is a bit too much to ask, due to the way DNS works with public IP addresses. However, I think I can emulate something similar to this by using IPTables to point different ports at different boxes. For instance, a request to mydomain.net:23 could be re-routed by the public facing box1 to port 21 on box2 - this much seems to be simple and fairly widely documented on the internet.

> **bab1 said:**
> 
One limitation of employing NAT is that only one host can use TCP port 80 in this scheme. If you had 2 web servers then 1 of those would have to use a different TCP port.

That is precisely the issue I'm trying to overcome by using one sub-domain per host. I would love to be able to route to individual machines via subdomains (eg ssh into box1.mydomain.net and box2.mydomain.net separately would be possible, both on the same port), but it seems that isn't possible!

Thanks for the help everyone!

---

