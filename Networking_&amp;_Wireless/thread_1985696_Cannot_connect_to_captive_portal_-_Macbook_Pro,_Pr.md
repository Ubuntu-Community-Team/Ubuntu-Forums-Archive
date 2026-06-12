---
title: "Cannot connect to captive portal - Macbook Pro, Precise"
date: 2012-05-23
forum: Networking &amp; Wireless
---

### Post by bbigam on 2012-05-23
I have not been able to find any recent support for this specific issue, so here goes:

My Wifi works with private Wifi networks with no issues, with security or not.
When I try to use a Wifi network with a captive portal (I.e. free Wifi at Starbucks or McDonalds [attwifi] or Panera Bread), the wireless attempts to connect for a while, then fails, but no error messages are generated except "Wireless disconnected."  When rebooting into Mac OS X 10.7, I can connect to those same wireless systems with no problems whatsoever.

I have:
Xubuntu 12.04 64-bit, kept up to date
MacBook Pro 8,1 (Late 2011 13-inch)
Broadcom BCM4331 wireless card (factory)
installed b43-fwcutter 0.15 from Main and firmware-b43-installer from Multiverse

I'm a recent "convert" to Linux so please be gentle, I want to learn to do things correctly!
Thanks for any help you can give.

Update: I upgraded b43-fwcutter and firmware-b43-installer from the Mpodroid PPA as suggested by some Mactel support pages.  No change in connecting to captive portals.  In fact, as it turns out I can't consistently connect to home, non-secured Wifi either - same problem, just not always.

Final update: Sorry, it turned out to be the same BCM43xx problem as everyone else.  Fixed!

---

