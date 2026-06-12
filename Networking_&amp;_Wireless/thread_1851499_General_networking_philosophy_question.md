---
title: "General networking philosophy question"
date: 2011-09-28
forum: Networking &amp; Wireless
---

### Post by koszta on 2011-09-28
Hi folks,
I love using Ubuntu, but there is another things I want wish you guys could help me with:

I have 2 servers and one external IP. The current status is this:
- first server is router/firewall/inside-company services
- second server is outside world services
- they are both connected to Internet (the 2nd one is connected via 1st one)
- I have all http (port 80) requests being redirected to 2nd server. I dont use https there at all (this is done by iptables)
- I have all httpS (port 443) requests being server on 1st server. I dont use http there at all. 

=> this is how I was able to use 2 web servers each serving part of my needs. Now I have this problem

=> I am about to buy new ticketing software and I need http and https being run on one server. Is there any way for me to accomplish this without having to get another IP from the provider? The only way (which is messed up) and I can think of (to kinda save myself some work) is to leave things as they are and just attach new cable (with new external IP) to one of the servers and run the software on that server (and the new IP).

Is there any other way? Do I absolutely have to get a new IP?

---

