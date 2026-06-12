---
title: "Proxy server without vpn or ssh"
date: 2011-07-08
forum: Networking &amp; Wireless
---

### Post by shazzed on 2011-07-08
I have been struggling to configure a squid proxy server on my ubuntu 11.04 VPS.

Following these instructions
[https://help.ubuntu.com/11.04/serverguide/C/squid.html](https://help.ubuntu.com/11.04/serverguide/C/squid.html)
it is all good BUT I don't want to have to SSH tunnel into the server. Just want to have a proxy set in my proxy server settings in firefox/chrome.

Even lock the proxy to certain static IP addresses so no one else can use it except IPs I designate.

1. Can this be done without a VPN or SSH tunnel ?

2. What is the best way to put some security on the proxy server ?

Any help or nudge in the right direction would be great.

Cheers
Shazzed

---

### Post by SeijiSensei on 2011-07-08
Use authentication with strong passwords.  Be aware, though, that without an SSH session, the passwords will be transmitted in clear-text.

[http://wiki.squid-cache.org/Features/Authentication](http://wiki.squid-cache.org/Features/Authentication)

---

