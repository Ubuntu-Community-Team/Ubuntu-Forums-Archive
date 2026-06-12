---
title: "Router or No Router... That is The Question?"
date: 2011-01-07
forum: Networking &amp; Wireless
---

### Post by garryconn on 2011-01-07
I currently have an Airport Extreme connected directly to my cable modem but have been wondering if I should actually connect direct to my proxy server first. The reason I am asking is because I run multiple web servers for web hosting and I have a proxy server setup that directs traffic to the appropriate computer based on domain names. 

As it is now, I have my router connected to my cable modem, and then all of my computers are connected thru the router. To me it would make more sense to have my proxy server be the first to connect and then thru a second ethernet card connect to the router. 

I also have a 5 port switch on order as well. So basically I'm asking for opinions now, in preparation for making some adjustments to my network and servers. Look forward to some responses.

---

### Post by Boondoklife on 2011-01-07
I really don't see a benefit to this, if anything it could be a detriment.

---

### Post by garryconn on 2011-01-07
Things run great 'as is' and I'm one to believe that it's best NOT to fix something that isn't broke. But, then again with Linux most of learning comes from breaking things. At any rate, partially another reason why I'm asking this question is because most of the diagrams I see on the web show pictures like this without a router:

[img]http://weblogs.asp.net/blogs/owscott/ReverseProxy_62C8B69C.jpg[/img]


Also, there's quite a few tutorials that teach how to build your own linux box router. Is there any true benefit to doing this? Or, should I keep my network setup how it already is?

---

### Post by Boondoklife on 2011-01-07
If you have a hardware router and it is not being a bottleneck then I don't see a reason to replace it. I would personally leave it the way it is. Most major companies will not host services on a router as if the service is compromised then they have the ability to take down your firewall and really do some nasty networking tricks.

I would leave your network the way it is unless you have a bottleneck you are trying to fix.

---

