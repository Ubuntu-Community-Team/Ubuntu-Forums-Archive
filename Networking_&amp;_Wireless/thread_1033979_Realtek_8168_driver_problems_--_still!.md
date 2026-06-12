---
title: "Realtek 8168 driver problems -- still!"
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by Phiwum on 2009-01-07
Hello.

I'm running 64-bit Ubuntu 8.10 on a new machine and I've followed the instructions to install the r8168 driver from realtek.  I'm still having problems.

The driver works, to a point.  That is, I can connect to my DHCP server and surf the internet for a while, but if I try any large downloads, the card just seems to crap out.  Nothing in dmesg that I can see, but the card stops receiving or sending packets as far as I can tell.

I can remove and re-load the module to return the card to a working state (until the next large download, of course).  

I'm at wit's end.  Any help would be greatly appreciated.

(NOTE: After posting this, and from idle curiosity, I decided to load the r8169 module --- the one that's supposed to be a bad choice for my card, the RTL8111/8168B Express Gigabit Ethernet controller.  The behavior was just the same as with the r8168 module!  No difference at all.)

---

