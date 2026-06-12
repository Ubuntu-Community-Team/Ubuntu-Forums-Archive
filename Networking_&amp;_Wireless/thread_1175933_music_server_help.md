---
title: "music server help"
date: 2009-06-01
forum: Networking &amp; Wireless
---

### Post by moore.bryan on 2009-06-01
long story short: i've successfully installed jinzora and, at home, can use it with my computer's ip. to use it outside my home, i decided to create a dns account to redirect my ip to a host. the problem is, it doesn't work. i've change my router (netgear) settings to allow dyndns, but no love. any ideas where i can start trouble-shooting?

thanks.

---

### Post by Iowan on 2009-06-01
> **moore.bryan said:**
>  i've change my router (netgear) settings to allow dyndns, but no love.By this do you mean you set up port forwarding - or are you talking about something else?

---

### Post by Mbradley1980 on 2009-06-01
have u just tried to access ur home from outside b4 as to make sure it works..?  

make sure u are able to connect to the compputers on your home network from outside ... setup a simple webpage on another machine and do the forwarding and make that work or such ... somthing simple to test first
?

---

### Post by moore.bryan on 2009-06-02
thanks for the responses. i broke my own first rule of posting: give as much detail as possible. mea culpa.

here's my setup...
i have an imac g4 &quot;flowerpot&quot; at home with a lacie 500gb external hd connected to it. on that machine, i've successfully setup jinzora and, at home, can access it with either [http://localhost/jinzora2](http://localhost/jinzora2) or [http://192.168.1.3/jinzora2](http://192.168.1.3/jinzora2). i read several &quot;how-to's&quot; about then setting-up dyndns to provide me a static host for the outside world--i.e., when i'm at work--and did that. 

comcast is currently giving me an ip of something like 68.39.16.198. i log-in to my new dyndns account, go to hosting services, and set-up a new host fore moore.ath.cx using the ip dyndns scanned from my imac. i then proceed to my netgear rangemax router and set-up the dyndns information requested and everything seems fine. 

alas, there's the rub... nothing works. at home, on my own network, i can use jinzora and stream my music with no problems using the ip given to the imac by the router; however, i can't gain access using my dyndns hostname.

does that answer any of the questions?

thanks, again, for any help you might have!    EDIT: okay, small change. i've dumped the mess that is jinzora and gone with gnump3d; however, i STILL have the same problem as before. i can connect with ALL machines on my home server, but can't connect with my setup dyndns of moore.ath.cx. i've even changed the port to a port which works just fine with deluge, but apparently not this. now, because  the port works fine with torrenting, i KNOW it can't be blocked by my isp (comcast), so what gives? please!

---

