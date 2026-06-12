---
title: "ip tunnel"
date: 2011-04-18
forum: Networking &amp; Wireless
---

### Post by swlnx on 2011-04-18
Hi I'm having a strange issue.
 
I have 2 linux servers in different locations.
I need to setup a ip tunnel. I follow this steps on both servers:
 
Server1:
 
ip tunnel add tun0 mode ipip local IP_Server1 remote IP_Server2 dev ethX
ip l s tun0 up
ip a a 10.10.10.1 peer 10.10.10.2 dev tun0
 
Server2:
 
ip tunnel add tun0 mode ipip local IP_Server2 remote IP_Server1 dev ethX
ip l s tun0 up
ip a a 10.10.10.2 peer 10.10.10.1 dev tun0
 
After creating the tunnel everything is ok, but after a time(maybe some  hours), I can't ping the other end of the tunnel (ping to IP_Server1 and  IP_Server2 is ok all the time; the connection to internet is very  reliable). I have tried "ipip" and "gre" mode, but same result.
 
If I ping from two servers the other end of the tunnel, the connection  is again established for some hours and ping is working in both  directions.(if I ping only from one side the ping is not working)
 
How can I resolve this issue for no longer having to log on both servers  to ping the other end of the tunnel? If I use an crondjob to ping the  other end of the tunnel at 2 hours everything is working fine for weeks,  but I need other solution.

---

