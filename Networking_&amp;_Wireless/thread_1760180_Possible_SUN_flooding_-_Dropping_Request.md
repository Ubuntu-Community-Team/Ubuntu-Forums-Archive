---
title: "Possible SUN flooding - Dropping Request"
date: 2011-05-16
forum: Networking &amp; Wireless
---

### Post by andy@andycrichton.co.uk on 2011-05-16
Hi 

I am doing some testing where I actually want to make a large number of socket connections (as in as many as possible) and am having difficulty with the SYN requests being dropped. I disabled syn cookies and now it's just dropping the requests.  I get the following message:

TCP: Possible SYN flooding on port 6666. Dropping request.

iptables -L shows no rules (I can't unload netfilter so I assume it's compiled into the kernel)

I also find that I can't establish an outbound connection so perhaps I'm filling something up somewhere. I manage to get about 190K sockets before I hit this. 

p.s. - Am testing something else not the ubuntu box, don't expect to realistically have that many connections for anything useful. 

Many Thanks for any thoughts.

---

