---
title: "Dell 1501 - Intel 4965 card works, 3945 doesn't"
date: 2010-09-25
forum: Networking &amp; Wireless
---

### Post by Bartender on 2010-09-25
I dual-booted a friend's Dell Inspiron 1501.  Ubuntu 10.04.  It comes with a Broadcom card.  Instead of screwing around with ndiswrapper or whatever, we replaced it with an Intel card because that seems to be the bomb-proof way to fix the problem.

Problem is, the Intel card is a 3945.  lspci doesn't even detect the 3945.  I swapped his 3945 for the 4965 in our Acer.  The 3945 works just fine in our Acer, and our 4965 works in his Dell.  lspci recognizes it, and the Dell saw our router immediately.  :confused:

So I swapped them back, careful to make sure the 3945 was installed correctly.  Sure enuf, his Dell acts like there's no card at all.

Anyone have any idea why a Dell 1501 running Ubuntu 10.04 can use an Intel 4965 but not a 3945?

UPDATE: Intel makes a 4965 MM1 and a 4965 MM2.  I don't know what's different between the two.  Our card is an MM1.  I read somewhere that the MM2 is for all-Intel chipsets but don't know for sure that's true.  The guy with the Dell 1501 (AMD parts inside) got onto his home network with an MM1.  Just passing this on for anyone who's thinking about doing the same.

---

