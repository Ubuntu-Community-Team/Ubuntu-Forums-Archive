---
title: "Frequent interenet disconnections from wirless Belkin G router."
date: 2009-10-05
forum: Networking &amp; Wireless
---

### Post by pandaberryy on 2009-10-05
Hello everyone, this is my first post, I've been searching for this problem and can't fix it so I decided to just join the forums and ask myself! 

So I'm not really Linux savvy but I've had Ubuntu 8.10 since this summer and sometimes my Internet is fine and sometimes I run into problems. Right now my problem would be frequent disconnections from the internet using the Bekling wirless G Router.

A home we have a dlink wireless router and my internet never disconnects, but here at my apartment we have a Belkin G Wireless router and my internet will just stop working at random times, I will usually have to just have to click on my wireless connections and reconnect for the internet to work again, sometimes I'll have to do this 3 or  times before it works again. I will find I am having to reconnect to our wirless connection several times an hour. 

Does anyone know how I can fix this so that my internet will just coninuously work instead of disconnecting every 20 minutes or so? 

Thankyou.

---

### Post by tsger on 2009-10-05
Has anyone else tried to connect using the router?  If so, do they have the same problems?  That could help narrow it down to whether it is a router problem or a computer problem.

---

### Post by pandaberryy on 2009-10-05
> **tsger said:**
> Has anyone else tried to connect using the router?  If so, do they have the same problems?  That could help narrow it down to whether it is a router problem or a computer problem.

Sorry I failed to mention that, unfortunately no one else has a problem connecting to this router. My room mate runs windows and always stays connected to the internet no problem.

---

### Post by bolex100 on 2009-10-17
I have the same problem with a Belkin N1 vision in Jaunty (only using G though). It doesn't actually drop the connection, just stops traffic.
No other devices (HP laptop/vista, PS3, XBO360. have problems.  I didn't have the problem with my old Linksys router (except it used to fall over completely a lot)

Here's there thing though:- Even though I was never successful in connecting to other computers on the network I have always been able to see them, and can still see them when the router stops.  I take that to mean that the switch is still working even when it stops me talking to the internet.

---

### Post by volaer on 2010-01-12
> **tsger said:**
> Has anyone else tried to connect using the router?  If so, do they have the same problems?  That could help narrow it down to whether it is a router problem or a computer problem.


I believe it's not due to Belkin. I also have Belgin G. When I was in intrepid, it works well and  fine. I never had problems. Now that I upgraded to Karmi Koala, the connection just stops and I can't reconnect again. I believe this is a bug or a programming program in Ubuntu. 

I need to reboot my laptop again in order to reconnect which pisses me off. The worst thing is, this happens to me at least 3 times in an hour. Grrr... any solutions?

---

### Post by dunbrokin on 2010-04-01
I am also having a similar problem with my Belkin.....changing the channel can sometimes help....I have 3 PCs all running 9.10 and two iPod touches....it seems impossible to get them all working at the same time on this router.....by OLD DLINK wireless ADSL Router had no problem. Also I find that, despite the very expensive price of the Belkin, its range is no better than my 5 year old DLINK......much disappointment in the household at, what could turn out to be, a very expensive piece of junk.

---

### Post by Fenris_rising on 2010-04-01
There are some Belkin routers that have a history of needing rebooting due to the connections dropping several times a day.

This is from bitter experience and weeks of frustration with the bloody thing.

For me a partial fix was changing the MTU of the router from 1432 to 1400. This cut down the number of disconnects for me but I eventually changed router brand. It should be noted that changing the MTU for me came about due to my ISP being a bunch of idiots and then finding a forum specifically about their lack of 'real' help and the solutions that people had found for themselves. My new netgear runs on 1400 but also has a DNS specified by me from the forum just mentioned as this helps netgears run better with my ISP. These settings are not those recommended by my ISP which cause all sorts of issues that they can't solve.

Also try getting an update to the routers firmware. This may help.

Routers nearby, if on the same channel, can also cause issues as mentioned above.

Try 

> iwlist scan

in terminal. This should pick up any wireless routers nearby and tell you what channel they are on so you can make an 'informed' change to your channel.

regards

Fenris

---

