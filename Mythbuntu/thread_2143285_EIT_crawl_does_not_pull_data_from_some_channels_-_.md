---
title: "EIT crawl does not pull data from some channels - manual tuning does"
date: 2013-05-08
forum: Mythbuntu
---

### Post by flecki on 2013-05-08
Hi All,

i have a DVB-C cable network setting and experiance the following minor issue - the automatic EIT crawl pulls data from some channels but from others not.

The fun thing is that if i tune to those channels in mythfrontend the database fills with the EIT from this transponder. 

I tried a full rescan, deleting and rescanning channels - problem stays the same.

Anyone an idea what i could do about it ?

Marcus

---

### Post by flecki on 2013-05-11
PS: I activated logging for EIT and database (mythbackend --setverbose database,eit) - the log looks OK so far, no errors to be seen...

---

### Post by alien878 on 2013-05-13
I've had this occasionally, but a re-scan has always fixed it.

Maybe a dumb question, but have you checked if "Use EIT data" is checked for the channels in question?  Also that mythfilldatabase is *not* running in parallel?

---

### Post by flecki on 2013-05-13
The use EIT checkbox is of course checked - Mythfilldatabase runs once a day automatically but exits the EIT part with the line "use EIT from provider is set - skipping" which is normal and OK

I was able to fix it by removing the use EIT mark from all channels i don´t like or can decode and then set them to invisible - since then EIT works for the channels i use.

I guess the EIT crawl hung up on some obscure channel or transponder i usually don´t use...

This does not solve the issue itself but at least my problem with it :-)

---

