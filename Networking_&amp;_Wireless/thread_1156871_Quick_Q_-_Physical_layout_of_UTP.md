---
title: "Quick Q - Physical layout of UTP"
date: 2009-05-12
forum: Networking &amp; Wireless
---

### Post by johnuk on 2009-05-12
I'm rewiring the house and want to put a network socket in each room, along with some other services like phone and TV. I was planning to make it neat and tidy by just packing it all into 25mm conduit and routing that through the joists, but I also realise interference may be an issue.

I was planning to use a 305m spool of UTP. Is that going to work is I also have the light / mains ring, TV and phone in the same conduit? Or am I going to continually bombed out with packet errors?

I could really do with answers only from people who've done it before given the scale and cost of the work involved.

Thanks for any help you can give! John

---

### Post by ProfDecoy on 2009-05-12
You'd be fine to run all your signal cables (TV, Phone, Ethernet) in the same conduit.  However, you'd want to try to keep your power lines reasonably separated from the rest where feasible.

What you want to avoid is a long run of your power lines that are parallel to your signal lines, that's how the most noise will will get onto your signal lines.

You might not notice any impact on the Ethernet cable (I've seen some pretty horrendous installations where 240V power lines had multiple Ethernet cables bundled in with them, performance was down but the data still got through).  However, you'd be more likely to notice the AC noise on your phone lines and TV signal.

---

### Post by johnuk on 2009-05-12
Thanks!

I found this in a magazine just after posting and going out to the dentist (I found it in a magazine in the waiting room);

[http://www.singlepointnetworks.co.uk/](http://www.singlepointnetworks.co.uk/)

Apparently I'll be fine even with that right up against the mains ring.

---

### Post by ProfDecoy on 2009-05-12
Hmm, looks interesting, but I guess I'm more of a traditionalist when it comes to some wiring.  Though, not having to rerun stuff at a later point is an added benefit if you can still get parts for it at that later time.

Anyway, good luck with your project and try to have fun doing it, other wise it's probably not worth doing... ;)

---

### Post by johnuk on 2009-05-13
After reading some more about it, I'm not sure it's anywhere near as exciting as it seems. It's not just one cable, it's a bunch of them in a bundle I think. And what's more, for some reason he's using things like a separate Cat 8 cable to carry a phone signal, which is massively overspeced and over priced. I should have known finding it in a home technology mag.

At first I thought they were somehow using the bandwidth of the cable to multiplex all the signal down one. But that's not it, it's just a separate cat 8 per service. Maybe I'm missing something, but that sounds incredibly stupid to me. Yep / no? :p

---

### Post by ProfDecoy on 2009-05-13
Looking at their page, it appears that they're essentially using each pair in the cable for something different.  In a typical Ethernet cable, you're only using 2 of the 4 pairs and in theory, could use the other 2 pairs to have a second connection on the same cable.  Which, is what it looks like they're doing with that.

Ick, Cat-8 cable?  I thought Cat-6 was bad enough in price.  I just did some short in room runs myself with Cat-5e.  A 1000ft box cost me about $70 USD, and another $10 for 100 RJ-45 tips.  Custom cables galore! :-)

---

