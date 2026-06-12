---
title: "Securing access to pptp VPN"
date: 2011-05-25
forum: Networking &amp; Wireless
---

### Post by Robbyx on 2011-05-25
I have been following the advice here:

[http://checkmytorrentip.com/](http://checkmytorrentip.com/)

See the FAQ tab

With vpn on I found an extra destination/ genmask  appeared in the route output:

10.22.0.1  255.255.255.255

I specified that ipaddress and genmask  in the routes window of the network manager IPV4 tab. I also ticked the ignore automatically obtained routes.

My intention is to stop the fall back to my unprotected non vpn route if the vpn line drops. Have I done it correctly?

The faq also advises:

> To achieve maximum privacy, disable DHT, uTP, UDP peers, and UPnP/NAT-PMP unless you know what you are doing. 

Is it advisable to follow that advice as well?

What else should I do to increase the security of the connection?


Since installing 11.04 I have not put back a firewall. Is that advisable and which one is more or less automatic in its configuration?

R

---

