---
title: "unable to browse while connected using wireless"
date: 2009-08-10
forum: Networking &amp; Wireless
---

### Post by kharat on 2009-08-10
Till some time before i was happly browsing using Dlink wireless card and Ubuntu HH 8.10.

Last week i was trying to connect using GPRS. I got connected but was unable to browse. While doing this picked the idea from net to del the default gw and add new for this (GPRS) connection (this is required to be 10.64.64.64). During this i beleive i fiddled with gw for my wireless connection and lost browsing but update-manager is working well (this is i beleive non-http). I have tried all settings in mozilla firefox, but no help.

Since this post is coming from another computer so not able to post (1) ifconfig (2) /etc/network/interface.
I would to be browsing through both connections (1) wireless (2) GPRS.
Can I be guided? 
TIA/vikas

---

### Post by Macchi on 2009-08-10
Kharat, 
I would suggest you to check the specific settings for your provider. To set up a new mobile broad internet connection you could delete existing connections and add a new ("fresh") connection. The network manager will normally prompt for the provider. Check later if the settings are correct!

My experience is that sometimes the NM had the wrong APN and I had to change it manually!








OBS: You certainly know this, but GPRS connections are the ultimate fallback solution: good to have but difficult for daily use. Certainly OK for small email messages but definitely too slow to access most modern websites due to the limited data transfer speed.

---

