---
title: "pptp vpn connects but will not route"
date: 2009-11-21
forum: Networking &amp; Wireless
---

### Post by acwal on 2009-11-21
I have configured a pptp tunnel and it connects as expected but traffic will not route to the other network. Unlike others, all of my traffic continues to route to the local network and gateway. I am assigned an IP on ppp0 and also get assigned a route that shows the inside address of the remote network. The resolv.conf file shows that I receive the DNS servers from the other network as well.
Have tried all sorts of settings including checking/unchecking the use tunnel only for computers on this network and adding routes with various gateways or none at all. The only thing that will ping is the local address for ppp0, I am not sure if the VPN server will offer ping responses but I can not ping anything on the remote network. I have a windows machine next to this one and it connects fine using the same connection and user/pass.
I am not sure what to try next or where to look for log files.

Ubuntu 9.10
the other end is a watchguard box set to accept pptp

---

