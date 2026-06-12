---
title: "SSH Tunnel and SOCKS5 Proxy Question"
date: 2013-05-19
forum: Networking &amp; Wireless
---

### Post by mitanc on 2013-05-19
I have currently setup a SOCKS5 proxy by creating a SSH Tunnel on a local Ubuntu server to a Linux based VPS.  I use polipo as a small proxy to pass the requests through the SOCKS5 proxy (DNS Resolution happens on the VPS side.)

Now, on the client end I use firefox and have an addon which has rules that enable it to use the proxy for some sites and not to for other.  My questions is, can I do the flitering on the server end?

Basically I want to have a request from clients machine (say 192.168.100.2) use the proxy server on my server (192.168.100.90) and the server can look through a whitelist, if it passes it send the request through the SOCKS5 tunnel.  If it doesn't pass, it just passes the request through the normal internet and sends the data back to the user.

---

