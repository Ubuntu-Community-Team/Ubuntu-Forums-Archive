---
title: "scte65scan woe's"
date: 2010-01-25
forum: Multimedia Software
---

### Post by darknight2183 on 2010-01-25
Hi All,
  I'm been using Mythtv for a while now, but recently moved and have Comcast as my service provider.  I've been running into problems trying to tune to the proper frequencies using the sctescan utility. This is what I've been getting when I run: scte65scan -V 0x0BC0 -f3 us-Cable-Standard-center-frequencies-QAM256 > mythvct.sql 
tuning 57000000hz.....no lock
tuning 63000000hz.....no lock
tuning 69000000hz.....no lock
tuning 79000000hz.....no lock
tuning 85000000hz.....no lock
tuning 177000000hz.....no lock
tuning 183000000hz.....no lock
tuning 189000000hz.....no lock
tuning 195000000hz.....no lock
tuning 201000000hz.....no lock
tuning 207000000hz.....no lock
tuning 213000000hz.....no lock
tuning 123012500hz.....no lock

It does this until it's cycled through the whole file.  I tried using some of the default scan files from dvb-utils but get the same error.  I also tried running the dvb-utils "scan" and got the same thing.

Any ideas on whats happening here???????

---

### Post by darknight2183 on 2010-01-26
sorry, command was scte65scan -v -p -f3 -V 3008 us-Cable-Standard-center-frequencies-QAM256 > mythvct.sql

---

