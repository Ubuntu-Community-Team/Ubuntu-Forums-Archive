---
title: "PPTP VPN can not connect to code.jquery.com"
date: 2012-11-05
forum: Networking &amp; Wireless
---

### Post by Boondoklife on 2012-11-05
I recently setup a vpn connection to a remote network but am running into the oddest issue, I am unable to connect to common CDNs such as code.jquery.com. Here is some information to set the stage:

Ping results:
I can ping the address remotely via ssh
I can ping the address locally without the VPN
I can ping the address locally with the VPN

Trace Route:
I can trace it successfully on the remote network via ssh
I can trace it successfully on the local network without vpn
I can trace it successfully on the local network with vpn

If I try to download the file:
I can download the file on the remote network via ssh
I can download the file locally without the VPN
I can **NOT** download the file locally with the VPN

The file in question is, "http://code.jquery.com/jquery-1.5.min.js", but this is far from the only one. As one can imagine this limits access to quite a number of sites that require jquery to work and also other CDN delivered payloads. When I try to load this and similar pages the browser will just spin indefinitely and eventually give a 404 error.

Other than this single oddity the VPN works great and I can browse the internet and even connect to the remote samba shares.

I am open to suggestions, thanks!

---

