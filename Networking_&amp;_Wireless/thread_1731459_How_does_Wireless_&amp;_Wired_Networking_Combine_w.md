---
title: "How does Wireless &amp; Wired Networking Combine when both are Active?"
date: 2011-04-17
forum: Networking &amp; Wireless
---

### Post by ScottCh on 2011-04-17
Hi Folks,

I configured my Ubuntu 10.10 desktop system for wireless networking initially.  When I found that the wireless network performance was weak (my wireless router is downstairs), I bought power line ethernet adapters and connected a 100baseT wired network using them.

I have not found a way to disable wireless and enable wired networking permanently using the network manager configuration (at least not in the standard gnome UI).  I can do this for a single session, but it is a bit tedious because turning off wireless resets the DHCP config (wipes resolv.conf).  So my system initializes with both wireless and wired networking active.

I have searched for information that describes how the Linux kernel handles having both forms of networking active, but have not found anything that spells it out.  Does wireless take precedence over wired, or vise versa?  Are both connections shared somehow, and if so how is the bandwidth of each managed?

This also concerns me because I often use my laptop this way.  I leave its wireless network up 100% of the time, but if I have a wired connection available I'll plug it in.

If there's a web page with the details please share the URL.

Thanks very much!

Scott C. in Cary, NC USA

---

### Post by bkratz on 2011-04-17
If you are using network manager to control your interface then it automatically selects the wired as a preference. See here.

[https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7)

---

