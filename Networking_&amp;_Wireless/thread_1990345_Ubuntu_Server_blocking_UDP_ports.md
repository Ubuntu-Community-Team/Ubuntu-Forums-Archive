---
title: "Ubuntu Server blocking UDP ports?"
date: 2012-05-29
forum: Networking &amp; Wireless
---

### Post by imotor on 2012-05-29
I have Asterisk 1.8 running on Ubuntu Server 11.10 and have an issue with SIP phone calls. I can make a phone call to the PTSN through SIP and it will ring, but as soon as the other side picks up, the call is dropped.

Trying to troubleshoot the issue: I noticed that nmap scans of the servers ports UDP 10000/20000 come back "closed" and a probe of port 5060 shows "open|filtered". Same result if I scan loopback from inside the server, scan the public IP, or scan the servers private IP from inside the network. Disabling UFW or enabling UFW and allowing 5060/10000-20000 makes no difference.

Question: Is it normal for nmap to show ports 10000-20000 closed when UFW is disabled?

Thanks

---

