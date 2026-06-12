---
title: "iptables busted or buggy in 11.10?"
date: 2012-01-29
forum: Networking &amp; Wireless
---

### Post by ulao on 2012-01-29
I use iptables and keep my other system behind my linux server. Since I upgraded to 11.10 its like all system have a really bad connection and some pages dont even come up. Form the linux box all is fine. Where would a person even start looking for a resolution for this?

---

### Post by 2F4U on 2012-01-29
If I where in your boat I would start by measuring the throughput (e. g. download rates) in several constellations:
1. From server to internet and from client behind server to internet.
2. Client behind server and firewall of server turned off
3. Client directly connected to internet and traffic not routed through server
4. Client behind server and client firewall turned off (if applicable)

---

### Post by ulao on 2012-01-29
I'm a little foggy on what you mean by throughput, like as in speed test?

I'm able to get normal speeds from server to internet. Also as long as the speed test site comes up, I'm ok from client to firewall to internet. Its just that the pages from some domains will not show up. Yet a tracert works fine. I dont have any reason to believe its a throughput in that sense. If I were to describe what I "think" is wrong I'd call it bad cache from iptables but I dont think there is such a thing. Local cache is cleared.

---

### Post by ulao on 2012-01-29
ok this did the trick.

iptables -t mangle -A FORWARD -p tcp --tcp-flags SYN,RST SYN -j TCPMSS --clamp-mss-to-pmtu

just needed to remember this is done in my boot script not a one time thing, duhh.

---

