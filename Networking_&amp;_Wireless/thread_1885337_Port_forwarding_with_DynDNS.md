---
title: "Port forwarding with DynDNS"
date: 2011-11-23
forum: Networking &amp; Wireless
---

### Post by sffvba[e0rt on 2011-11-23
Hi,

For my home web-server I can't use port 80 so I have set-up port forwarding on the router to an alternative port (13555).

This works great if someone uses [www.mydomain.com:13555](www.mydomain.com:13555) but isn't ideal :)

I am using DynDNS as I don't have a static IP and from this ([http://dyn.com/support/webhops-and-redirections/#ports](http://dyn.com/support/webhops-and-redirections/#ports)) it would seem that what I want to achieve should be possible... except I have read this little bit several times and I am not understanding it completely (or even semi-completely).

I am not exactly sure how to do this, if anyone with some experience could nudge me (or hold my hand and lead) it would be greatly appreciated.  Also if there is a better way I am all ears :)

Please ask more info as needed, as I don't know what my be needed.

FTR - domain: nlsthzn.com (and if you go to nlsthzn.com:13555 you should see the apache welcome page).


Regards
404

---

### Post by papibe on 2011-11-23
Why can't you use port 80?

Does your ISP restriction won't allow it, or your router is not able to do it?

Kind Regards.

---

### Post by Derek Karpinski on 2011-11-23
[http://dyn.com/support/wizard/](http://dyn.com/support/wizard/)

Click on 'An alternative port' and follow the directions.........

Or use no-ip.org instead which allows you to use only one DNS name that will redirect ports without assigning new dns names.

---

### Post by sffvba[e0rt on 2011-11-23
> **papibe said:**
> Why can't you use port 80?

Does your ISP restriction won't allow it, or your router is not able to do it?

Kind Regards.

Seems it is blocked on the ISP level...

> **Derek Karpinski said:**
> [http://dyn.com/support/wizard/](http://dyn.com/support/wizard/)

Click on 'An alternative port' and follow the directions.........

Or use no-ip.org instead which allows you to use only one DNS name that will redirect ports without assigning new dns names.

Thanks... I ran that wizard several times and not once did I notice 'An alternative port' ... even after your post it took me 5 minutes >.<

Well I am happy to report that [www.nlsthzn.com](www.nlsthzn.com) should now be working :)


404

---

### Post by Derek Karpinski on 2011-11-23
Where did you get your domain name from?  And how did you link it to dyndns if you bought your domain from some other place like go-daddy?  I'm interested in doing it myself.

BTW-your webserver is working....(It works!)

---

### Post by sffvba[e0rt on 2011-11-23
> **Derek Karpinski said:**
> Where did you get your domain name from?  And how did you link it to dyndns if you bought your domain from some other place like go-daddy?  I'm interested in doing it myself.

What I had to do was change the DNS servers on GoDaddy for my domanin to the ones of DynDNS after I configured everything on DynDNS's side...

A few hours later and it was working (For the record, I am using Dyn Standard DNS for $30 a year...)



Cheers 
404

---

### Post by nothingspecial on 2011-11-23
[attach]207820[/attach]

---

### Post by sffvba[e0rt on 2011-11-23
> **nothingspecial said:**
> [attach]207820[/attach]

Thanks :)

Pity with the current setup that nlsthzn.com will time out :/


404

---

