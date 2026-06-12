---
title: "mythbuntu, clock change and mythweb"
date: 2010-04-10
forum: Mythbuntu
---

### Post by vancheese on 2010-04-10
Hi people

My mythbuntu set-up worked great in winter time - My XMLTV is set +1 hour and mythweb works too.
However, when the clock changed, the system became out of sync

So for I have tried with no success 

1) changing the time zone to one +1 on the computer
2) changing the PHP timezone (/etc/php5/apache2/php.ini) to local zone and to local +1. Apache restart
3) Changes the XMLTV  to +2 

After each other these, mythfilldatabase has happened
All have failed - Any suggestions

Andy

---

### Post by nickrout on 2010-04-11
> **vancheese said:**
> Hi people

My mythbuntu set-up worked great in winter time - My XMLTV is set +1 hour and mythweb works too.
However, when the clock changed, the system became out of sync

So for I have tried with no success 

1) changing the time zone to one +1 on the computer
2) changing the PHP timezone (/etc/php5/apache2/php.ini) to local zone and to local +1. Apache restart
3) Changes the XMLTV  to +2 

After each other these, mythfilldatabase has happened
All have failed - Any suggestions

Andy

you haven't told us anything really.

where are you timezone wise?
what timezone is your machine set to?
what is the result of the date command?
what version of ubuntu are you on?
what version of tzdata?

---

### Post by vancheese on 2010-04-12
Ok, I'm in CET and my XMLTV is GMT. Date was fine and I'm on Karmic mythbuntu and there was no tzdata installed and when I installed it, everyting worked fine!

Thanks for those excellent questions

---

### Post by nickrout on 2010-04-12
Odd that tzdata was not installed, it should be installed as a matter of course.

---

