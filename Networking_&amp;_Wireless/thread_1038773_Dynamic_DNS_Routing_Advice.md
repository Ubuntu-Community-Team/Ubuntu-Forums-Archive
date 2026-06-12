---
title: "Dynamic DNS Routing Advice"
date: 2009-01-13
forum: Networking &amp; Wireless
---

### Post by chrisolof on 2009-01-13
I'm interested in how others out there pull this setup off, since I'll soon be setting it up (somehow!):

[http://something.dyndns.org](http://something.dyndns.org) -> My Tomato Router -> [http://192.168.1.2](http://192.168.1.2) (web server one)
[http://somethingelse.dyndns.org](http://somethingelse.dyndns.org) -> My Tomato Router -> [http://192.168.1.3](http://192.168.1.3) (web server two)

Currently I've got one web server in my local area network (under my Tomato router), which gets all port 80 traffic forwarded to it from any WAN request - and one dynamic dns address pointing at the router.  I basically want to double this setup so that two distinct machines connected to my router can host their own websites at different dynamic dns addresses.

I'm thinking this is do-able by somehow examining where each port 80 request originates - but I could be totally off-track on that.

Thanks in advance if anyone has any advice!

---

### Post by Iowan on 2009-01-14
I'll leave myself a note to check on name-based virtual hosts when I get home (bookmarked on that machine). Maybe not exactly what you're asking, but the information may be helpful.

[Here]("http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/") is the link.

---

### Post by mshenoy4573 on 2009-01-15
well since 192.168.1.2 and 192.168.1.3 will be getting traffic thru the same router the dyndns will see a single IP address(external ip) so I am not quite sure how this will work...

ill try the setup and let you know....

you can definitely have the web servers running on different ports to route traffic from the router for instance 80 and 88 but to separate the traffic from external ip to two separate ip's is something I am not aware of.....
its definitely worth looking into

---

### Post by chrisolof on 2009-02-07
To Iowan:  Thankyou for the great how-to!  I think that would work if I was hosting websites on my router, but what I'm doing requires the router to split and forward port 80 traffic to two different IP addresses (physically different web servers) on the LAN depending on the domain name requested.

If I don't end up finding a solution to accomplish that, and I'm having little luck so far, I'll probably end up doing both sites on the one server and use that name-based virtual hosting to accomplish it.

To mshenoy4573:  Tomato firmware does allow me to have two Dynamic DNS accounts (maybe more) configured in the router - so that's where my original idea sparked.  I think it's probably ok on the dyndns.org site to have two dyndns addresses pointing at the same IP.

I'm almost thinking that I could have my more public-oriented server on port 80 and the other development-only machine accessible over https (port 443).  The only issue would be that my development server ssl certificate would cause browsers to present ominous warnings to visitors - but that's a different topic.  In fact I think I'll give that a shot and see how it goes.

---

