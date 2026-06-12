---
title: "Mythweb external access"
date: 2010-11-02
forum: Multimedia Software
---

### Post by Brasil on 2010-11-02
Hi all, I'm trying to get my mythweb to be accessible external to my home intranet. I've got it set up to work fine within my home and now I'd like to be able to access it from work.

A few points
Firstly, I've set it up on port 81. [http://www.canyouseeme.org/](http://www.canyouseeme.org/) says port 81 is open, and when I access it internally I use [http://192.168.1.3:81/mythweb](http://192.168.1.3:81/mythweb) . The router is configured to forward port 81 though and UFW is set up to allow access to port 81.

When I access externally, I get "can't establish a connection to the server'.

I also followed the instructions here [http://www.gossamer-threads.com/lists/mythtv/users/392999](http://www.gossamer-threads.com/lists/mythtv/users/392999).

Obviously I'm missing something obvious. Would anyone be able to advise?

---

### Post by Brasil on 2010-11-04
Bueller? Bueller?

Anyone got a tip?

---

### Post by Brasil on 2010-11-09
Well, this one remains unresolved. Thanks for your time everyone, if I figure it out I'll post the response back here in case someone else strikes the same problem.

Cheers,
-Travis

---

### Post by Brasil on 2010-11-15
I "resolved" this - everything was actually working fine, I was just trying to access via the external IP address while on my network, and the router was preventing it. Go off the network and it all worked fine :)

---

