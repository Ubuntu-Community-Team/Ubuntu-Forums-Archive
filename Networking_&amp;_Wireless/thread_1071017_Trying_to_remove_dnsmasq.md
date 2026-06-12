---
title: "Trying to remove dnsmasq"
date: 2009-02-15
forum: Networking &amp; Wireless
---

### Post by Pollox on 2009-02-15
I'm trying to get my computer to stop using OpenDNS.  I believe it started doing that when I installed dnsmasq.  However, when I uninstall dnsmasq, I can't get any web pages to load on my home network.

---

### Post by Pollox on 2009-02-24
Bump.  Anyone have any ideas?

---

### Post by mpokrywka on 2009-02-24
I guess you installed dnsmasq on your router/gateway?
Two questions:
1) do you have internet access on your gateway? (ping -c1 google.com) How it is configured? (dhcp? dsl modem static ip?)
2) when you remove dnsmasq does computers on home network can reach gateway at all? (ping -c1 ip.of.your.router) (I guess you use dnsmasq as dhcp server and this will fail)

I think best way to fix your problem would be to fix dnsmasq configuration not to use opendns (or probably it is configured as your gateways dns)

---

### Post by Pollox on 2009-02-24
> **mpokrywka said:**
> I guess you installed dnsmasq on your router/gateway?
Two questions:
1) do you have internet access on your gateway? (ping -c1 google.com) How it is configured? (dhcp? dsl modem static ip?)
2) when you remove dnsmasq does computers on home network can reach gateway at all? (ping -c1 ip.of.your.router) (I guess you use dnsmasq as dhcp server and this will fail)

I think best way to fix your problem would be to fix dnsmasq configuration not to use opendns (or probably it is configured as your gateways dns)

I installed it on my laptop, not on the router, as part of trying to follow the instructions on [http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/]("http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/") to do local dns caching. Unless dnsmasq is installed by default, as I don't remember if I actually had to install it, but I'm assuming I did.  At the time, it seemed to correct an issue I was having on my home network with many web pages not loading.  Since then, I experienced an issue with many web pages not loading when connected to my school's wireless vpn network, which I thought might be caused by the local caching thing, so I undid all of the steps except removing dnsmasq, but to no avail.  If dnsmasq is not to blame for that, then simply configuring it not to use OpenDNS would work for me (I don't care for when I get redirected to an OpenDNS search page), but I haven't been able to figure out how to actually do that.

When I remove dnsmasq from my computer, I am still able to connect to the router (ping -c1 192.168.1.1 gets a reply with no packet loss) but ping [www.google.com](www.google.com) gives the error ping: unknown host [www.google.com](www.google.com).

---

### Post by Iowan on 2009-02-24
What does your router use for DNS? If you get address via DHCP, you can also check */etc/dhcp3/dhclient.conf* to verify that it requests DNS servers (and it *may* be set to use the prepend option to inject OpenDNS.

---

### Post by Pollox on 2009-02-24
> **Iowan said:**
> What does your router use for DNS? If you get address via DHCP, you can also check */etc/dhcp3/dhclient.conf* to verify that it requests DNS servers (and it *may* be set to use the prepend option to inject OpenDNS.

My router uses DHCP.  There's a line in dhclient.conf that says "prepend domain-name-servers;".  I don't really know much about that file.  Should that line say something different?

---

### Post by Iowan on 2009-02-25
From my dhclient.conf file:```
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;

```The "prepend" line is commented out.  IF I wanted my preferred DNS servers to be checked before whatever my DHCP server "recommends", I could include them in that line.  For example: **prepend domain-name-servers 208.67.222.222,208.67.220.220;** would check OpenDNS first.

---

### Post by Pollox on 2009-02-26
> **Iowan said:**
> From my dhclient.conf file:```
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;

```The "prepend" line is commented out.  IF I wanted my preferred DNS servers to be checked before whatever my DHCP server "recommends", I could include them in that line.  For example: **prepend domain-name-servers 208.67.222.222,208.67.220.220;** would check OpenDNS first.

Thanks.  That worked for stopping using OpenDNS.  Unfortunately it still didn't fix the issues I was having when on a vpn connection, but it doesn't seem that dnsmasq is the culprit there, so I will start a separate thread on that.

---

