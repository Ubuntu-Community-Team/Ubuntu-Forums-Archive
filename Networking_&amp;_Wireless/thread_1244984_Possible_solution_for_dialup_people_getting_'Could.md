---
title: "Possible solution for dialup people getting 'Couldn't find interface ppp0' error"
date: 2009-08-20
forum: Networking &amp; Wireless
---

### Post by rustycar on 2009-08-20
I know almost nobody is using dialup any more, however I just got it working for my mom, for whom I just installed Ubuntu 8.10 (which gave me much grief on a Dell Optiplex 320 - I advise against wasting much time putting linux on that monster).

Anyway, I installed 8.10 on a generic PC and spent way too much time trying to get ppp to work.  After switching to a USRobitics USR 5637 USB modem (which worked pretty well under Linux!), I got the above 'Couldn't find interface ppp0' error.

Symptom: KPPP sees the modem fine, dials out, connects to the ISP.  Then, pppd takes over and dies with that un-helpful message.

My solution:  Run KPPP as root.  (Apparently somebody didn't have permissions needed to talk to pppd or something strange like that)

Yes, its a stupid solution, but I didn't have time to figure out why ppp0 didn't have the permisisons I needed, and it worked.

There are LOTS of reasons you can get that error - but at least here is one possible reason and workaround.

I just hope this saves someone ELSE the hassle I had!

RustyCar

---

### Post by theozzlives on 2009-08-20
> **rustycar said:**
> I know almost nobody is using dialup any more, however I just got it working for my mom, for whom I just installed Ubuntu 8.10 (which gave me much grief on a Dell Optiplex 320 - I advise against wasting much time putting linux on that monster).

Anyway, I installed 8.10 on a generic PC and spent way too much time trying to get ppp to work.  After switching to a USRobitics USR 5637 USB modem (which worked pretty well under Linux!), I got the above 'Couldn't find interface ppp0' error.

Symptom: KPPP sees the modem fine, dials out, connects to the ISP.  Then, pppd takes over and dies with that un-helpful message.

My solution:  Run KPPP as root.  (Apparently somebody didn't have permissions needed to talk to pppd or something strange like that)

Yes, its a stupid solution, but I didn't have time to figure out why ppp0 didn't have the permisisons I needed, and it worked.

There are LOTS of reasons you can get that error - but at least here is one possible reason and workaround.

I just hope this saves someone ELSE the hassle I had!

RustyCar

Log on to the Internet as Root?! There's gotta be a less dumb way of doing it.

---

### Post by Iowan on 2009-08-20
> **theozzlives said:**
>  There's gotta be a less dumb way of doing it. Lets call it "a _safer_ way of doing it". ;)

---

