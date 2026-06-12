---
title: "Netgear WGT624 v3 dns resolve slow"
date: 2010-08-23
forum: Networking &amp; Wireless
---

### Post by hil on 2010-08-23
I used ubuntu 9.1 and 10.04 with my Netgear WGT624 v3 11g router. There were problems resolving host names on the internet. The DNS resolving would be fine for 10 seconds and started to be slow (>4 seconds) when resolving new websites at firefox and at console using ping [www.google.com](www.google.com). An obvious repro is using SYstem > Administration > Network tools > Ping > enter network host [www.google.com](www.google.com) > check unlimited requests > enter.

It took me   3 hours to find it was my router's problem. Disabling ipv6 or changing to Google's or OpenDNS's servers did not help. Please be aware this netgear router. I replaced the router with netgear WNDR3300 firmware V1.0.29_1.0.29NA using the exact same network settings (WAN,LAN,WiFi) and the problem went away. Please be aware of the router you are using could cause bad or slow DNS resolving on ONLY Linux but not on Windows.

If anyone knows how to fix my WGT624 router, please post here. I am thinking about just selling it for $20 on Craigslist.

---

