---
title: "PPC as router"
date: 2009-08-11
forum: Networking &amp; Wireless
---

### Post by ForMar on 2009-08-11
Hello,

Ive been having tons of trouble with my router and its inability to handle moderate amounts of traffic so in hopes of not spending much money I came up with the idea to put some use to an old PPC laying around the house. Its an iBook mid 2005 PPC. I was hoping that I could use it as a router. I know that I'm going to need to add one more network card to it.

**Question:** 

Is it feasible to use an iBook G4 mid 2005 PPC as router running ubuntu server? Will it run well and handle packets at a fast speed? And finally can someone with limited knowledge of linux, tables, and and anything to do with networking get it done?   

Your time, advise, and help is very appreciated 

Anthony

---

### Post by paulisdead on 2009-08-11
That's way more than powerful enough for iptables.  There's plenty of router/firewall howtos out there, and the setup would be nearly identical as on x86.  If you intend to have a GUI installed, you might want to look into firestarter.

Your current router, is it also your dsl/cable modem?  If so, this probably won't help much unless you replace it as well, if this is supposed to sit between your LAN and the internet.

---

### Post by ForMar on 2009-08-11
> **paulisdead said:**
> 

Your current router, is it also your dsl/cable modem?  If so, this probably won't help much unless you replace it as well, if this is supposed to sit between your LAN and the internet.

First thanks for the post!

It does not double as a cable modem i have a separate "thing" for that. But I might use the router as a access point (wifi) or will that just cause the same problem. 

Thanks
Anthony

---

### Post by paulisdead on 2009-08-11
It's not impossible for it to cause the same problem, but probably won't.  You have tried removing it from the picture and having your PC plugged directly into the cable modem, to see if the problem persists?  If you're still seeing the problem, it's not the router.  It could be the cable modem, or something else on the line upstream from you.  Just try to narrow down where the issue is, if you haven't already.

If the Mac has a Linux compatible wifi card, or you can get one easily for it, you might want to just set it up as the access point as well.

---

