---
title: "How to connect directly to modem after removing router/switch?"
date: 2009-03-06
forum: Networking &amp; Wireless
---

### Post by Tuvok41 on 2009-03-06
Hi, ive been using Ubuntu since October, I luv it, but my router is blocking too much ICMP coming from me, and I am sure the router is the problem, when i go to browse webpages it is taking for ever to show up and some times it cant resolve at all.
So I want to switch from using router to direct connection to the modem, but my problem is everytime I try to connect without the router it doesnt work I tried with network manager changed the dns host, but it still didnt configure the connection automatically and Im wondering if there is something else I should do? I have all info about default gateway and subnet mask, multicast and mac address of the NIC. What should I do to get it to work? 
All help is much appreciated and if there is a how to please link me to it, I have looked and search and everything I found is about wireless or router connection, didnt see nothing about switching back from computer/router/modem to computer/modem.
Thx in advance for all your help.

---

### Post by Iowan on 2009-03-06
IPv6 could cause similar symptoms.  The "Remove IPv6" link in my sig is a little dated.  As far as bypssing the router... If the modem is capable of being a DHCP server, you could enable that.  Second, the modem may have "locked onto" the router's MAC address.  Cycling power to the modem (turning it off, waiting a minute, then turning it back on) may let it acquire the MAC of your computer instead of the router.

---

### Post by Tuvok41 on 2009-03-07
Thanks for the reply IOWAN, indeed I never powered it off, why didnt I think of that lol. I will check back in if it does resolve my problems.

---

