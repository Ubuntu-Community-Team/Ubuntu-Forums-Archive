---
title: "bypass router DNS caching with public DNS(but keep DHCP)"
date: 2010-12-18
forum: Networking &amp; Wireless
---

### Post by Dreki on 2010-12-18
My router is crap. If I use DHCP it sets all the computers DNS to itself and all DNS requests get cached in the router.  It even starts to loose some DNS request if to many are made at once.  On my windows PCs this isnt a problem I just set DNS to google's public DNS servers (8.8.8.8 & 8.8.4.4) and bypass my router and ISP alltogether but when i go to pref>network_connections i have to either set DHCP or manual, there is no option to set DHCP with custom DNS.
I'm sure there must be a way to do this in terminal, can someone tell me how?
I'm using ubuntu 10.10.
thanks in advance!

---

### Post by Calimo on 2010-12-18
Hi,

In the file /etc/dhcp3/dhclient.conf, you can add dns in the "prepend domain-name-servers" line (comma-separated). Mine reads like this (removed all the comment lines starting with #):

```
option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

send host-name "<hostname>";
prepend domain-name-servers 127.0.0.1,195.186.1.162,195.186.4.162,195.186.4.111,195.186.1.111,195.186.4.110;
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, domain-search, host-name,
        netbios-name-servers, netbios-scope, interface-mtu,
        rfc3442-classless-static-routes, ntp-servers;
```
The 127.0.0.1 in the prepend domain-name-servers is because I installed dnsmasq to cache DNS requests and gain a bit of time: this is especially useful if you use DNS servers far from you. If you don't have dnsmasq, remove localhost from this line!

Hope it helps!

PS: "prepend domain-name-servers" will put the IPs in /etc/resolv.conf. But don't edit resolv.conf because it is overridden frequently (boot, and maybe each time you reconnect but I'm not sure of that)

---

### Post by Dreki on 2010-12-19
thanks a bunch calimo that helps a lot

---

