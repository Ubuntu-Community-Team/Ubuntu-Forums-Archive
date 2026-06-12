---
title: "&quot;Transparent Proxying&quot; with &quot;ssh -D&quot; SOCKS Proxy?"
date: 2010-04-13
forum: Networking &amp; Wireless
---

### Post by Geremia on 2010-04-13
Hello,

On my laptop I have an ssh SOCKS proxy running through en5 on the localhost port  1080 (ssh -fND 1080 my_proxy_host). How do I share this proxy connection  with other machines connected to my laptop's DHCP server via the Ethernet (en0) interface such that  those machines don't have to be setup to recognize a SOCKS proxy? I assume I must  use natd, ipfw, and bootpd. I tried using natd's "-proxy_only" and "-proxy_rule  server 127.0.0.1:1080" arguments but no no avail.

Any help appreciated

Thank you

---

