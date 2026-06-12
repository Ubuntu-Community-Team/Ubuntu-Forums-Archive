---
title: "BIND (server) and Dynamic DNS Updates"
date: 2012-01-20
forum: Networking &amp; Wireless
---

### Post by matmbl on 2012-01-20
Hi,

I'm trying to find information (step by step guide) or even if it's possible to update my DNS server dynamically!

My scenario is that I host my own DNS server for my own domain in the cloud (ubuntu 8.04.4 LTS) which also hosts my web site, email forwarding, etc, etc. I'd like to be able to get my router or my ubuntu server at home (on the end of a DSL line behind a dynamic IP address) to update my DNS server with the current IP address of my home connection, creating an domain something like home.mydomain.com.

I've done some searching but can only find results related to DHCP updates or regular DNS (client) setups. Any help would be most appreciated.

matt

---

### Post by silverglade00 on 2012-01-20
You could get a dyndns.org name for it and install the client. That will update your dyndns.org name with the new IP address. Then you can set up a CNAME in your DNS server to point to the dyndns.org IP. I have either had too much or not enough coffee, so let me know if I wasn't clear. It made sense to me.

---

### Post by matmbl on 2012-01-20
Thanks silverglade, I've done this in the past but something's always gone wrong, my router updating the dyndns server to frequently so i get banded or I something changes somewhere (someone buys the company I'm using, which also happen last year or the year before!) and it stops working and I don't notice it until i'm traveling and i need to vpn home (which is too late)!

I guess if I have to I'll cron rsh into the dns server and run a script which updates the zone files and kicks the bind process every couple of hours, but I'm sure there's a 'neater' solution ;-)

To give you an idea, I just upgraded my vm ubuntu from 8 LTS to 10 LTS, the uptime was 752 days. I like to get things working once ;-)

---

