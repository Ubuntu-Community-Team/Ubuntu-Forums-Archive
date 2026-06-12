---
title: "Using ubuntu as &quot;passive&quot; port forwarder - orb functionality"
date: 2009-07-03
forum: Networking &amp; Wireless
---

### Post by kjetilbmoe on 2009-07-03
Dear experts,
I try to get my ubuntu (1) to work as a connection point for another computer (2) being behind a firewall. My idea is that (2) initiates a connection to (1), so that I can connect to (1) with a third computer. I have been looking into using inetd or a proxy server, without luck. Any suggestions?

(Winamp Remote (accessing music collection remotly) uses such a solution, so I know it is in some way possible)

Thanks.

---

### Post by munky99999 on 2009-07-03
[http://en.wikipedia.org/wiki/Squid_%28software%29](http://en.wikipedia.org/wiki/Squid_%28software%29)

---

### Post by kjetilbmoe on 2009-07-03
Thanks, but I cannot see how a reverse proxy can get me to the computer behind the firewall. Is it really so? Computer (1) and (2) are miles apart (not in same network). The idea is to connect a third computer to (1) which - the way I see this - uses an existing connection to (2) to access this. Is still squid the way to do this you think?

---

