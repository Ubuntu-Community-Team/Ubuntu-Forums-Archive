---
title: "Tracking bandwidth used with Linksys WRT54G Router"
date: 2009-12-07
forum: Networking &amp; Wireless
---

### Post by samalex on 2009-12-07
Hi,

This isn't a Linux question per say, but I hope someone in here may know the answer.  We're about to build a house in a neighborhood that I just found out didn't have any wired Internet providers, so our only option is to go with one of the wireless providers like Verizon.  Given most of these only give you about 4 GB of traffic a month I'd like to see if there's anyway I can see how much bandwidth we're using now through the router, which is a Linksys WRT54G.  I say this because all our internet traffic goes through this, so if it can do it that's the simplest way.

I'd rather not flash the firmware because we're putting all our cash towards getting our current house to sell, and my wife will kill me if I brick our current router ;-)  But if doing this is the only way and there's slim to no chance of hosing the box, I'm game to research it.

Thanks for any suggestions.  As best as I can tell there's no SNMP capabilities or bandwidth stats, but just incase I'm missing something please let me know. 

Take care --

Sam

---

### Post by harry71194 on 2009-12-07
Verizon only gives 4 GBs worth of traffic per month?! That's crazy that ISPs are still limiting traffic in 2009.


Though you are hesitant to flash the firmware, I'd recommend dd-wrt. I have a similar router, worked fine on it.

If/when you install dd-wrt, you can find the bandwidth stats @ [http://192.168.1.1/Status_Bandwidth.asp](http://192.168.1.1/Status_Bandwidth.asp)

---

