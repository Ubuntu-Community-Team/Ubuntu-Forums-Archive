---
title: "cat6 cable"
date: 2011-10-19
forum: Networking &amp; Wireless
---

### Post by Drenriza on 2011-10-19
Hi guys.

Intersting subject. I've studied network for sometime now. And then today a colleague of mine are discussing length on Cat6 cable. I say u can run it 100 meters at max without repeating the signal. They say 220 meters.

So i have searched the web. And apparently some say 100 meters (330 feet) and others say 220 meters (720 feet?). But i could not find the industry standard for the cable. So which is it 100 meters or 220 meters?

Kind regards :p

EDIT.
As i thought Cisco (where i get my knowledge :p) also says 100 meters. So where does this 220 meters come from?

---

### Post by bkratz on 2011-10-19
> **Drenriza said:**
> Hi guys.

Intersting subject. I've studied network for sometime now. And then today a colleague of mine are discussing length on Cat6 cable. I say u can run it 100 meters at max without repeating the signal. They say 220 meters.

So i have searched the web. And apparently some say 100 meters (330 feet) and others say 220 meters (720 feet?). But i could not find the industry standard for the cable. So which is it 100 meters or 220 meters?

Kind regards :p

EDIT.
As i thought Cisco (where i get my knowledge :p) also says 100 meters. So where does this 220 meters come from?



here is an interesting article--it appears that cat6 hasn't been totally ratified yet perhaps the reason for the discrepancy?! 

wireville.com/news/CAT%206%20Copper's%20Last%20Stand.pdf

That appears to be old information. This looks promising

[http://www.lanshack.com/cat6a.aspx](http://www.lanshack.com/cat6a.aspx)

---

### Post by Jonathan L on 2011-10-19
> **bkratz said:**
> here is an interesting article--it appears that cat6 hasn't been totally ratified yet perhaps the reason for the discrepancy?! 

wireville.com/news/CAT%206%20Copper's%20Last%20Stand.pdf

That appears to be old information. This looks promising

[http://www.lanshack.com/cat6a.aspx](http://www.lanshack.com/cat6a.aspx)

Hi

My understanding is that Cat 6, like the predecessors, was specified in terms of things like crosstalk limits, and that to qualify, a given cable must exceed the specification for 100m cable, and this will get you 1000baseT at 100m.  But this only lets 10Gbase-T go a certain distance (55m) and only if the installation is according to guidelines and under some conditions the limit is 37m.

A good explanation is here 

[http://www.ampnetconnect.com/documents/Options%20for%2010-Gigabit%20Cabling.pdf](http://www.ampnetconnect.com/documents/Options%20for%2010-Gigabit%20Cabling.pdf)

The TIA charges for its standards, but a summary is [http://www.cat6.com/overview/standards.aspx](http://www.cat6.com/overview/standards.aspx)

Cat6a is more confusing, but I understand it gets you 10Gbase-T at 100 m.
[http://www.ampnetconnect.by/web/Microsites/ISO_Cat6a/6a_Facts/ClassEa_vs_Cat6a/](http://www.ampnetconnect.by/web/Microsites/ISO_Cat6a/6a_Facts/ClassEa_vs_Cat6a/)

The documents at Fluke for how you test this are good
[http://download.flukenetworks.com/Download/Asset/2545521_0000_ENG_D_W.PDF](http://download.flukenetworks.com/Download/Asset/2545521_0000_ENG_D_W.PDF)

Fluke also makes excellent documents for inserting into your contracts for the testing requirements (as part of a sophisticated strategy for selling testers), if you search for "Category 6A field testing requirements" in their downloads section.

As the cabling market is very competitive, you may well find that a given manufacturer makes cable which they claim has acceptable performance at greater lengths, but I know of nothing which is over double or mentions 220m for anything.  If you've got a mind to it, it's very educational to actually measure some of this, and what you'll find is that if you put the speed down or can accept higher than normal packet loss, you can go surprisingly far.

Hope that's helpful.

Kind regards,
Jonathan.

---

