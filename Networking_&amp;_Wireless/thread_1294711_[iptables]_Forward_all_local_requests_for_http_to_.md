---
title: "[iptables] Forward all local requests for http to one website"
date: 2009-10-18
forum: Networking &amp; Wireless
---

### Post by mhueting on 2009-10-18
Hi!

I want to redirect all http requests made from my computer which runs iptables to one site, say, disney.com. To clarify, this is a local issue: my computer isn't a gateway, I just want to redirect all requests from my computer to port 80 on any ip to one single ip. Is this possible using IPtables?

---

### Post by mhueting on 2009-10-19
I solved my own problem. To redirect all http traffic to ubuntuforums.org:

iptables -t nat -A OUTPUT -p tcp -j DNAT --to 91.189.94.12

Works like a charm :)

---

