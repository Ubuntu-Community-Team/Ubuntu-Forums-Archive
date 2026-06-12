---
title: "Help with Squid Acceleration Config"
date: 2009-06-12
forum: Networking &amp; Wireless
---

### Post by MichaelJohannes on 2009-06-12
Hello,

I'm wondering if someone can give me a hand with my Squid configuration. Here's what I'm trying to do:

1) Set up a Squid proxy so users can connect to it for testing approximately 50 websites on an internal web server (IIS 6.0) rather than landing on the page on the internet.

So far I have the website working on port 80 using the following custom lines in my config (everything else is default):

```
cache_peer 192.168.10.31 parent 80 0 no-query originserver name=myAccel
acl ten_network src 192.168.10.0/24
acl our_sites dstdomain www.website.com
http_access allow our_sites
cache_peer_access myAccel allow our_sites
cache_peer_access myAccel deny all

http_port 80 accel defaultsite=www.website.com

http_access allow ten_network
```

This config works on the default port 80. All I'd like to do is add the capacity to have a number of different websites internally on different ports. In IIS I can specify whichever internal port I'd like and firewall (NAT) to that port. But I'd like to have this capacity without leaving the network.

Ex.
[www.website2.com](www.website2.com) --> IIS port 81 (for example)


The issue I'm having is trying to figure out a simple way I can have a different http_port with a vhost or default site pointing to a different website on my IIS server. The idea is that my fifty sites can be hit using a proxy add-on like Foxy Proxy without traversing the internet (for web development).

Any suggestions are greatly appreciated. (if this is in the wrong section please let me know).

Mike

---

