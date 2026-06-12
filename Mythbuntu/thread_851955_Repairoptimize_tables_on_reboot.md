---
title: "Repair/optimize tables on reboot"
date: 2008-07-07
forum: Mythbuntu
---

### Post by lingenfr on 2008-07-07
I live in a place with rather frequent power outages. Most of the time the power outage occurs when someone is watching TV, etc. This leaves me with one or more mythconverg tables corrupted. So then I either use phpmyadmin or mythweb to repair the tables and I normally optimize while I'm at it. This works fine when I am home, but leaves the family without TV if I am on the road. I am thinking that the right thing to do would be to setup my system to automagically repair/optimize tables when it boots. Is there a simple way to do this?

---

### Post by mrand on 2008-07-07
> **lingenfr said:**
> I live in a place with rather frequent power outages. Most of the time the power outage occurs when someone is watching TV, etc. This leaves me with one or more mythconverg tables corrupted. So then I either use phpmyadmin or mythweb to repair the tables and I normally optimize while I'm at it. This works fine when I am home, but leaves the family without TV if I am on the road. I am thinking that the right thing to do would be to setup my system to automagically repair/optimize tables when it boots. Is there a simple way to do this?
Howdy,

Unfortunately, that's just putting a small band-aid on a rather major cut.  One of these days, the damage will be in just the right spot that it may not be repairable.  Then you sure enough will have an unhappy group of people at home!

If you can at all afford it, buy a UPS that has a status output which can be feed the computer so that it can shut down gracefully.  Perhaps a refurbished UPS (old unit with a newish battery)? I'm lucky enough to live close to a company that does that and the prices are VERY reasonable because I don't have to pay shipping fees.

   Marc

---

### Post by lingenfr on 2008-07-07
I plan to do that as well. Regardless, I don't think a repair/optimize on boot will hurt anything.

---

### Post by lingenfr on 2009-04-11
Still have this issue. I don't see a problem with running a repair/optimize on mythconverg and mysql everytime I start mythbackend. Does anyone know how to do that? Thanks.

---

### Post by joshoekstra on 2009-04-11
I don't know if mysql is already started, but you could try to put it in /etc/rc.local. Put in the repair/optimize command from the contrib and you should be good to go.

EDIT: did my suggestion do the trick?

---

### Post by lingenfr on 2009-04-18
> **joshoekstra said:**
> I don't know if mysql is already started, but you could try to put it in /etc/rc.local. Put in the repair/optimize command from the contrib and you should be good to go.

EDIT: did my suggestion do the trick?

I don't know how to do what you recommend.

---

