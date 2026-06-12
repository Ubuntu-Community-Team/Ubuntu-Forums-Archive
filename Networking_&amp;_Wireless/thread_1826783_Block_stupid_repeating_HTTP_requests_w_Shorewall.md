---
title: "Block stupid repeating HTTP requests w/ Shorewall"
date: 2011-08-17
forum: Networking &amp; Wireless
---

### Post by amanisdude on 2011-08-17
Oookay. For some stupid reason that I cannot comprehend, McAfee Anti-Virus (McSvHost.exe, specifically) on my laptop keeps htting my Apache server with HTTP/1.0 requests and totally JAMS UP my Apache access logs. Why it does this every twelve seconds, no less, is beyond me, but I need to find a way to deny HTTP/1.0 requests on the local network.

While I could conceivably block my laptop IP to port 80 totally, this isn't feasible, as I use my laptop for web dev and need to view my website through the LAN. McAfee also hits with different source ports (it actually moves up the port number chain sequentially), so I can't block it using that either.

Anyway, it would be much appreciated if anyone could help me quickly write up a Shorewall rule that will just block HTTP/1.0 requests on my local network if that's possible (not WAN, 'cause I use that). Any help would be awesome. Thanks all! ^_^

---

