---
title: "Can't access certain sites via wifi-tethered 3G"
date: 2012-03-01
forum: Networking &amp; Wireless
---

### Post by DrPotoroo on 2012-03-01
I am having a problem connecting to certain sites via a wifi hotspot I have created on my stock Samsung Galaxy S2 on the Telstra NextG network, using the built-in hotspot option. General sites work fine, but it seems that I can't access secure sites and nor can I use ssh. These sites, and ssh, work fine from the phone directly.

I have read elsewhere that this could be an issue of the MTU size. I have tried adjusting this (sudo ifconfig wlan0 mtu XXXX) without any improvement.

I really don't know if this is an ubuntu problem, or a problem with my phone, or a problem with telstra blocking ports on tethered connections, or ...?

I don't know what MTU sizes I should by trying, except that maybe smaller (< 1450 or <1200?) might be better? But I don't know if precise numbers will make a difference. I read a method for testing different possible MTU values in windows using ping, but this doesn't seem to work in ubuntu since it never tells me if my packets are getting fragmented. Has anyone had similar problems, or found a solution? Help please!

I'm running ubuntu 11.04.

---

### Post by DrPotoroo on 2012-03-05
Even if nobody can directly help answer my problem, it would be a HUGE help if someone else with a Galaxy S2 can tell me if they have used it as a wifi hotspot with ubuntu and successfully connected to secure sites (e.g., a google account), or SSH. Knowing whether others are/are not experiencing my problem would help me narrow down the source of my problem.

---

