---
title: "Help me! ICS Xp-&gt;Ubuntu"
date: 2006-06-05
forum: Networking &amp; Wireless
---

### Post by doughnut on 2006-06-05
hi everyone! 

Im a bit of a newbie when it comes to Linux so i appologise if i sound like a goose! 

Im trying to share my broadband connection from an XPmachine with this, my dual boot ubuntu/xp machine.

ICS is working fine on XP->XP but on XP->ubuntu it seems to have problems.

Ubuntu recognises theres a network cable but the connection is 'idle' and i am unable to access any web pages etc. ive tried getting firefox to auto assign proxy's etc and also tried manually(correctly may be another question) but this doesnt seem to work.

so in conclusion i guess what i want to know is how do i share my XP machines broadband connection with my ubuntu one.

my network looks like this:
<XP with Broadband conn>-----------Crossover Cable------------<Ubuntu>

would really appreciate any help:)

---

### Post by dmizer on 2006-06-05
your best, cheapest, headacheless solution here is to just go pick up a hub (not a router, a hub).  you can probably find one at a resale store for super cheap if you want to go that way, but even brand new they are extremely resonable.

but for the immediate issue, in ubuntu, what is the output of ifconfig?  do you see an eth0 (or eth1 or some such), or just an lo?

---

### Post by doughnut on 2006-06-08
cheers for the advice dmizer.

got it all goin nicely as it is now tho. (still with just Xover cable)

i just needed to manualy assign some IP addresses and proxys but tis all good.

cheers for the help tho!

:D

---

