---
title: "request to package Ardour 2.0"
date: 2007-05-01
forum: Multimedia &amp; Video
---

### Post by wbrown on 2007-05-01
Greetings: 

The audio appication Ardour released 2.0 yesterday (April 30,2007) [http://ardour.org/node/895](http://ardour.org/node/895) .  The current release in fiesty is 0.99.3-1.  Does someone know of a howto link for packaging the updated build so that it can be submitted?  Or how else do I request should I request the package to be updated.  I assume some of the Ubuntu Studio people can answer this? 

Thanks.
Bill.

---

### Post by dfreer on 2007-05-01
this might help you make a .deb:
[http://linuxdevices.com/articles/AT8047723203.html](http://linuxdevices.com/articles/AT8047723203.html)

---

### Post by mrfuzzemz on 2007-05-06
Have you tried to compile it from source?

---

### Post by MetalMusicAddict on 2007-05-06
Ardour2 will be available from the Ubuntu Studio repos soon.

---

### Post by kelvin spratt on 2007-05-06
IT is available right now from [http://www.getdeb.net/](http://www.getdeb.net/)  just download and double click its that easy

---

### Post by mrfuzzemz on 2007-05-06
Before I noticed you posted the link with the deb (thanks, by the way!) I sat and compiled the whole thing after getting all the dependencies. It wouldn't start because jackd wouldn't start.  I did some research and the installed the lowlatancy kernel.  This still didn't work.

I then installed qjackctl and jack started. Ardour2 was then able to start.

---

