---
title: "Shared net between Xp and Ubuntu?"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by Captain Kremmen on 2009-10-31
Hey all...

New to Ubuntu as of last night (can't get much newer than that) and considering it took me 2 hrs to work out how to install ueagle-atm and configure it.. please be gentle :)

OK, I had a search for it.. but didn't really see an answer, so.....

I want set up my netbook(xp) and my main pc Ubuntu to use a shared net conection, presumably this would mean networking Windows to Linux.. Is this even possible?

All anwsers to be a simple as possible please :D

Thx.

---

### Post by mikewhatever on 2009-10-31
Haven't tried it myself, but looks really good.
[http://www.ubuntugeek.com/creating-an-adhoc-host-with-ubuntu.html](http://www.ubuntugeek.com/creating-an-adhoc-host-with-ubuntu.html)

---

### Post by psycho5 on 2009-10-31
Simple answer is yes, i did it with my brother sharing the connection to my ubuntu but vista was the OS. so it was vista to ubuntu. But, I think it shouldn't be that difficult, this was a hsdpa connection and we were sharing through wifi

---

### Post by Captain Kremmen on 2009-10-31
Thx, guys...

but want to try a wired network with the dsl net conection coming from xp to Ubuntu.... or visa versa..

It's getting them to handshake that seems to be causing me the probs...

Anyways.. I'll keep searching, but if anyone has experience with this, I'd like the benefit of it :)

---

### Post by Iowan on 2009-10-31
See if [this]("https://help.ubuntu.com/community/Internet/ConnectionSharing") one helps.

---

### Post by Captain Kremmen on 2009-10-31
Hmm..thx Iowan, but not quite there yet :), it uses 2 nics for the example...but all I really need to do is join an xp netbook to an ubuntu pc via crossover cable, then add a usb dsl modem to either side and have the net connection accessable from either/both machines.

Lol.. I'm not really surprised I'm having trouble doing this.. I can't even do this properly on two windows machines :O

:/

---

### Post by viper250 on 2009-10-31
first your dsl modem must be able to support multiple connections.
second if you are using your ubuntu pc as a gateway it will in effect become a net server and must be able to provide an isp number that your netbook can connect to via dhcp.
if your dsl modem only has 1 ethernet connector you can only use one computer at a time anyway so if you have a multiple connection dsl modem you do not need to connect through the ubuntu pc.

---

### Post by Captain Kremmen on 2009-10-31
> **viper250 said:**
> first your dsl modem must be able to support multiple connections.
second if you are using your ubuntu pc as a gateway it will in effect become a net server and must be able to provide an isp number that your netbook can connect to via dhcp.
if your dsl modem only has 1 ethernet connector you can only use one computer at a time anyway so if you have a multiple connection dsl modem you do not need to connect through the ubuntu pc.

Hmm...this could well be a solution to a different problem, but I'm not entirely sure that it's relevent for mine.

I'm using a usb modem... the only use for ethernet cards I have is to link my comps together in a network.

Thx though :)

---

