---
title: "NovaT 500 low noise amplifiers"
date: 2010-02-07
forum: Mythbuntu
---

### Post by tonycollinet on 2010-02-07
Mythbuntu 9.10

I'm using a nova t 500, and while working fine, I get some picture dropouts, and some clicks/pops during recordings.

I have enabled the LNA's but have never been convinced they are actually on. As a test I have tried disabling them:
> options dvb-usb-dib0700 force_lna_activation=0

In both options, and options.conf.


After a hard restart - they are making absolutely no difference. I am still getting around 78% signal strength as before.

How do I check if the LNA's are actually working? How can I disable them as a test.


Thanks.

---

### Post by gwagchunks on 2010-02-08
I tried this on a Wintv nova-td 500 and it did not seem to do anything. When I tried switching it off, dropouts got so bad I ended up reloading myth.

---

### Post by wyliecoyoteuk on 2010-02-08
Without that entry in options.conf, I get no signal at all.
However, if you have a strong signal, signal amplifiers may actually overload the tuner and make the errors worse.

Our local signal kept changing in strength last year when they were making changes to the transmitter, sometimes I needed 2 signal amplifiers ( external ones, not the LNAS), sometimes one, and sometimes none, it was infuriating!

It has settled down now, I still need one amplifier and the LNAs on.

---

