---
title: "VPN -&gt; autoset proxy"
date: 2013-02-23
forum: Networking &amp; Wireless
---

### Post by alwe84 on 2013-02-23
Hi,

to connect to my university's network, I have to use a proxy server and a vpn connection.

The vpn (vpnc) is working fine with the Network Manager. I now would like to automatically set the system proxy, when the vpn-connection comes up. And disable it, when the vpn-connection is down. 

I played around with dispatcher.d scripts but i can't manage setting the proxy. 
I tried setting environment variables and adding the proxy settings to /etc/environment.

The problem is that I have to logout and back in to apply those settings. 

So is there a way of setting a system proxy from a dispatcher.d script so I don't have to log out?

Cheers,

alwe84

---

