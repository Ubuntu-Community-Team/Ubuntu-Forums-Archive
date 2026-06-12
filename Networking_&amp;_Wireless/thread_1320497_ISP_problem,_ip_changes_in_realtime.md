---
title: "ISP problem, ip changes in realtime?"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by Elijah on 2009-11-09
Hi, 

Recently my IP has been changing much too frequently.. and in realtime too(!) how is this possible? I never reconnected from the ISP to get a diff IP address, I just find out my IP has changed after a website (any) boots me out and tells me I have to re-login because my IP has changed. This is too frustrating and annoying to be working on a site and then suddenly I get logged out within seconds. 

I used ip checkers and found out that my IP is alternating to what seems to be a proxy server.. I used several IP checkers and two sites that detects a proxy, both confirmed my ISP is using a proxy... but my ISP denied they are using one .. which should I believe? or is the iSP support doesn't know what he's talking about?

---

### Post by lensman3 on 2009-11-09
The DHCP address is given out with an expire time.  After it expires it has to be renewed.  Your ISP can renew it.  

In a file found at "/var/lib/dhclient" is a copy of your lease.  It has the lease time in this file.  Mine is up on the order of 3 days.  It can be set for a lot less, but puts a high load on the dhcp server.

If your time is over 86400 seconds (one-day), then your dhcp client is doing a renew.  

I can see an ISP going to short times because it would cut down on spamming virus infected PC's.  When the IP number is renewed then all the ports that were in use would become invalid, so a spamming virus computer would have to reset all links.

Hope this helps.

---

### Post by Elijah on 2009-11-09
Thanks for the info, 

What's strange is that this happens every minute or so... alternating to let's say an IP ending in .249 then when I refresh the ip checker site I get a .50, I refresh again and then it goes back to .249.. really weird

.50 is what's detected to be a proxy

---

