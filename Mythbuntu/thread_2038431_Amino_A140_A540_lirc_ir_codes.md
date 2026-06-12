---
title: "Amino A140 A540 lirc ir codes?"
date: 2012-08-06
forum: Mythbuntu
---

### Post by davidstoll on 2012-08-06
Does anyone have the ir codes to control a Amino A140 or A540 (IPTV set-top box) with an irblaster in MythBuntu?

Thanks

---

### Post by anonymousdog on 2012-08-06
If you have the actual remote control, you can easily generate the codes in less time than it takes to wait for an answer here.

---

### Post by davidstoll on 2012-08-06
> **anonymousdog said:**
> If you have the actual remote control, you can easily generate the codes in less time than it takes to wait for an answer here.

Well, I guess that would work.  What is it called (so I know what to search for).  I've searched for that type of thing before, but I guess I didn't use the right key words.

Or if you have a direct link to the info, that would work too.

Thanks for your help.

---

### Post by anonymousdog on 2012-08-06
irrecord will help you to create a lirc hardware config file for that remote.  Read the man pages on irrecord and ensure that lirc is already setup for your receiver/blaster.

---

### Post by tells1977 on 2012-09-03
Did you get lirc to change the channel on your Amino STB?  I captured the code using irrecord, but irsend does not work for me.

---

### Post by nickrout on 2012-09-03
> **tells1977 said:**
> Did you get lirc to change the channel on your Amino STB?  I captured the code using irrecord, but irsend does not work for me.

all my reading seems to indicate you should be able to bypass the amino box and do IPTV straight onto your mythbox, although is the provider encrypts you will need to use the STB.

eg

[http://www.gossamer-threads.com/lists/mythtv/users/500488#500488](http://www.gossamer-threads.com/lists/mythtv/users/500488#500488)

[http://www.mythtv.org/wiki/SureWest_IPTV](http://www.mythtv.org/wiki/SureWest_IPTV)

---

