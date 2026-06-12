---
title: "Set type of DVB card"
date: 2014-06-22
forum: Multimedia Software
---

### Post by nuesel2 on 2014-06-22
Hello,
I've install the DVB card "DVBSky T982" on an Ubuntu 14.04. The drivers load successfully as the two DVB devices are availble:

#ls /dev/dvb
adapter0  adapter1

My problem is, that this card has two tuners built in and supports two types of DVB, DVB-C and DVB-T. So I can feed in two DVB-C or two DVB-T signals, or one of both.
I would like to use these adapters from TVHeadend. Both adapters are detected and I can search for DVB-T channels. But I cannot set the type of one adapter to DVB-C. Is there a way to tell Ubuntu the type of the card manually?

Regards,
Nuesel

---

### Post by xc3RnbFO8P on 2014-06-22
I don't  know if you can start it like this:
> tvheadend /dev/dvb/adapter0
> tvheadend /dev/dvb/adapter1

it works with Kaffeine

---

### Post by nuesel2 on 2014-06-22
Hello Ringi,
unfortunately, TVHeadend works as service and is configured over a web interface. Thus, adding command line parameters will not work.
By the way, I would like to use both adapters, but I would like to use different signal sources.

Regards

---

