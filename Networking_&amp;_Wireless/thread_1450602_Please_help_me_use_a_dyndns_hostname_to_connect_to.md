---
title: "Please help me use a dyndns hostname to connect to my ubuntu server"
date: 2010-04-09
forum: Networking &amp; Wireless
---

### Post by big_danmahony on 2010-04-09
[LEFT][/LEFT]I'm not really sure how to word this, so if any further clarification is needed, please ask.

I've recently set up an Ubuntu server and from within the network I can do several things like: log in via SSH, transfer files via FTP, and remotely control Torrents from other computers. My end goal is to be able to access these services by using my dyndns hostname (example.dyndns.org)from an external network.
When I type my dyndns name in my web browser it opens up my router page.
How would I set things up so that I can just type my dyndns hostname to point directly to my server, instead of the router page?

All computers are connected to a router which is connected to an ADSL modem, with automatically assigned I.P addresses.

If anyone could help me I would be truly grateful.

---

### Post by tava0002 on 2010-04-09
Since example.dyndns.org resolves to your routers external address, you need to configure your router to forward the various traffic to your internal server.  So if you go to example.dyndns.org in a browser your router will forward port 80 traffic to your server and same for ssh port 22 traffic.

---

### Post by big_danmahony on 2010-04-11
Thanks for that,
 I forwarded port 22 (both UDP and TCP and it seems to find my server but I cannot log in from the program I use for ssh (Putty) it says "access denied"
Would this mean I have forwarded the ports incorrectly? or maybe another feature of my router is preventing me?
I used [[COLOR="Red"]this[/COLOR]]("http://portforward.com/english/routers/port_forwarding/Dlink/DSL-502T/SSH.htm") guide, is there anything else I need to know?

---

### Post by Knacker on 2010-04-11
> **big_danmahony said:**
> Thanks for that,
 I forwarded port 22 (both UDP and TCP and it seems to find my server but I cannot log in from the program I use for ssh (Putty) it says "access denied"
Would this mean I have forwarded the ports incorrectly? or maybe another feature of my router is preventing me?
I used [[COLOR="Red"]this[/COLOR]]("http://portforward.com/english/routers/port_forwarding/Dlink/DSL-502T/SSH.htm") guide, is there anything else I need to know?

I don't have a lot of experience with this sort of thing, but two things you should check, if this still isn't working. First, make sure that the internal IP address (i.e. 192.168.*.*) that your router is forwarding to is the right one (i.e. the one that is currently assigned to your server)...unless you have yoru router assigning a static to your server, it could have changed.  Still, if you can connect from within your network using the same internal IP that that router is forwarding to, then that's not the problem. 
Second thing to try: sometimes things get funny when you try to connect back into your own network (via, say, dyndns service) from your network. So, try to connect using your neighbour's wifi connection. 
Again, not really experienced with this stuff, but one of these might do the trick. Good luck.

---

