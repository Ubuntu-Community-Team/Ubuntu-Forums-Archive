---
title: "Can't find attwifi (Starbucks) unsecured with 8.10"
date: 2009-05-19
forum: Networking &amp; Wireless
---

### Post by Dngrsone on 2009-05-19
I have 8.10 installed on a Pavilion DV2000 series laptop.  The wifi worked immediately and I can access th internet through my wifi at home, no problem.

I am on the road right now, however, and the Ubuntu installation can't see the attwifi at the local Starbucks (I am using Win XP to access it at the moment), though it does see the local secure wifi (Actually, there are two unsecured networks Ubuntu is not detecting here).

A quick search through the forums netted me nothing, though I might not have a good set of search terms.

Any idea what I might be able to do to get the Ubuntu to find and connect to the free wifi?

---

### Post by Dngrsone on 2009-05-21
NO ideas, huh?  Well, I guess I will have to live on XP for a couple more days...

---

### Post by blindeinstein on 2009-06-03
You might give wicd a try. 

sudo apt-get install wicd

I was having trouble getting network manager to keep me logged in at my Starbucks wifi. After the switch, no problems.

---

