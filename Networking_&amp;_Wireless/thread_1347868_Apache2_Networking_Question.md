---
title: "Apache2 Networking Question"
date: 2009-12-06
forum: Networking &amp; Wireless
---

### Post by TheDelChop on 2009-12-06
Hey Guys,

I'm not sure if this is the right forum to post this question, it might be better placed in Applications, but I'm gonna start here.

I'm trying to setup my Apache server, and I'm not having too much success at the moment.  To make things worse I can't say I'm positive that the requests are getting routed properly through my DNS to actually get to my apache server. 

The reason I say this, is because the contents of my apache server logs (located in /var/log/apache2) are empty.  

So, my first question is this:  Is there a place where requests to my server (not my apache server, but any incoming request to the ubuntu o/s) are logged or stored?

It is entirely possible that my DNS and my router setup are the reason for this problem, but I need a way to better isolate the issue and this seems like a good start.

Thanks guys,

Joe

---

### Post by gordintoronto on 2009-12-06
Have you told your router to forward port 80 to the local IP address where Apache resides?  (Likely 192.168.1.something.)

Can you point a browser on another local computer on your network at that IP address?  You should be able to test the web site that way.

Do you have a commercial connection with your ISP?  Many ISPs don't let home users run web sites.

---

### Post by TheDelChop on 2009-12-06
> **gordintoronto said:**
> 
Do you have a commercial connection with your ISP?  Many ISPs don't let home users run web sites.

You are exactly right, if I change the listening port to something else it works just fine.  Thank you so much. 

Joe

---

