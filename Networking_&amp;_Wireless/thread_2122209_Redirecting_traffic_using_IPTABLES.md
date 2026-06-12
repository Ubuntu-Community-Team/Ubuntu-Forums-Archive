---
title: "Redirecting traffic using IPTABLES?"
date: 2013-03-04
forum: Networking &amp; Wireless
---

### Post by badatz on 2013-03-04
Hello all,
 
I am fairly newbie to the whole ITPABLES/SQUID thing, and quite frankly I am very confused because I am not sure which tools I need to be able to accomplish my goal.
 
This is what I am trying to accomplish… I would appreciate if someone could please tell me which tools/services needed to be used.
 
Let's say that a user in US wants to view restricted video content in Germany. I would like to setup some sort of a re-director to transfer the request from US User --> German "proxy" server --> German video site. I am using the term "Proxy" but I really don't need to cache any traffic, just to re-direct it.
 
If we put the whole DNS a side for a minute, is it possible using IPTABLES to do the following:
 
Any TCP/IP traffic that comes from let's say 24.0.0.0/24 (or a single IP) to German "proxy" server will
get automatically redirected to German video site using the server IP address so the Video site will think the traffic comes and goes from Germany?
  
Regards,
Jack

---

