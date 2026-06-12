---
title: "HOW TO: UK TalkTalk customers with distrowatch problem."
date: 2012-01-25
forum: Networking &amp; Wireless
---

### Post by Double.J on 2012-01-25
Hi all, 

This thread is for customers of the ISP TalkTalk in the UK experiencing problems with the distrowatch(DW) website.

This is a bit sporadic as it appears to depend upon which package you have with the UK ISP TalkTalk(TT). From what I can tell, if you're on the premium (20M/bit) packages, this shouldn't affect you. 

The problem is with the TT DNS server. The fix is just to change your DNS server. Popular alternatives are openDNS and Google Public DNS... I'm sure you can find more ;)

I shall focus on OpenDNS because their website is very user friendly for those not sure what they are doing, and has router-specific guidelines :) 


To the problem. All you need to do is change your DNS Server address from the router (most likely 192.168.1.1) to the address of your chosen DNS server.

These settings are often around the LAN and DHCP settings. For example, on the HG521 router, you go to 

Advanced>Basic>LAN> 

the value you want to change is the primary DNS server address and the secondary address.

For open DNS these are
```

Primary DNS server address:	 208.67.222.222	 
Secondary DNS server address:    208.67.220.220 
```

For google
```

Primary DNS server address:	  8.8.8.8	 
Secondary DNS server address:     8.8.4.4
```

Then just erase browsing data restart router and computer.

Hope it helps!
____________________________________________

Note: OpenDNS offers a number of paid services and registration.. you do not need to do any of this to fix the problem. If you want router specific information, or more information on OpenDNS, you do have to register on their site, but again you should keep choosing the free option - any button with a price per month on it is the wrong one ;)

---

