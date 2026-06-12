---
title: "Why did I need to configure the VPN like this?"
date: 2011-03-08
forum: Networking &amp; Wireless
---

### Post by Another Monkey on 2011-03-08
I wanted to run a PPTP split-tunnel between my home and my office.
So I set that up in NetworkManager, selected "Use this connection only for resources on its network" under "IP4 Settings" and connected.
No joy, it would connect but I couldn't ping anything.

I added an entry into the routes under "IP4 Settings" pointing company IPs to the internal company router and it started working, but no name resolution.

I then changed "Method" to "Automatic (VPN) addresses only", added the company DNS and the search domain as "company.local".  Name resolution is now working and the split-tunnel seems to be OK too (only work traffic looks like it is going over the VPN).

My question is - why did I need to fiddle like this?  Why wasn't "Use this connection only for resources on its network" enough?  Am I just being a bit dim and having to do all this is perfectly normal, or is something (e.g. corporate firewall) possibly being a bit restrictive?

I'm still trying to find out what all the options actually mean/do...just haven't found the correct page yet (I have read [VPNClient]("https://help.ubuntu.com/community/VPNClient#Using%20NetworkManager")); and it irritates me to not understand the "why".

---

