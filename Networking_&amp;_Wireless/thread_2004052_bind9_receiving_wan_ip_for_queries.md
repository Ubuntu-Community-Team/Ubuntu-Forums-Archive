---
title: "bind9 receiving wan ip for queries"
date: 2012-06-15
forum: Networking &amp; Wireless
---

### Post by bibble235 on 2012-06-15
I have a simple set up one modem/router, server and tons or PCs and wireless devices.

I have been trying to set up bind so I can use xxx.mydomain.com on my PC at work and at home.

At work it is 121.x.x.x (WAN IP)
At home it is 192.x.x.x (LAN IP)

I have done this successful but with one issue. I use a dynamic IP for my server and use zonedit to keep it up to date. This means the WAN IP changes each time the modem is reboot or my ISP has an off day.

My issue is the queries to my DNS come in with the WAN IP and not the LAN IP when at home.

E.g. my mobile sends a query with 121.x.x.x and this is denied because I have the line  

allow-query {192.168.1.0/24;};

in the bind9 configuration.

A workaround for me is to have
allow-query {121.x.x.x; 192.168.1.0/24;};

However I would prefer not to have to maintain this.

I have a TP-LINK TD-W8960N router/modem

Thanks,
Iain

---

