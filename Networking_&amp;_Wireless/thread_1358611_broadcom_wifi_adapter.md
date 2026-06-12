---
title: "broadcom wifi adapter"
date: 2009-12-18
forum: Networking &amp; Wireless
---

### Post by amishera on 2009-12-18
I chose one laptop which I very much want to buy but the problem is it has a broadcom adapter. From what I have heard, broadcom adapters are not very friendly with linux distros that is why I have always disregarded any laptops with broadcom adapters. My previous laptop had intel adapter and it  worked smoothly. I figure setting up network(ie hardware issue) is the most painful thing for using any linux distro. Now should I buy this laptop? Also I am not sure whether future linux distros like ubuntu would continue to support older hardwares like this.

Thanks.

---

### Post by mikewhatever on 2009-12-18
It's hard to advise about the older hardware, since you haven't told us what the hardware is. All hardware will become obsolete eventually, made by Intel, Broadcom, or another company. As for Broadcom wireless cards. they have much better these days, albeit through closed source drivers. Once again, you haven't mentioned the model, but chances are, it will works out of the box. Mine did just that, and it's BCM4312.

---

### Post by northd_tech on 2009-12-19
Hello Amishera.  It would help if you told us the Laptop Model and Broadcom chipset in question.  There is a proprietary &quot;STA&quot; driver out now that seems to work very well (I'm using my Broadcom 4321AG under Ubuntu 9.04 to type this wirelessly right now).  The 4321AG is sometimes reported as a "4328" by Linux though.  From my experience, the 4311, 4312, 4321, and 4322 Broadcoms all have methods to get them working under Ubuntu. 

I haven't seen a Broadcom yet that won't work with "ndiswrapper" and the Windows XP/Vista/Seven driver method.  Just be glad it's not a year ago- the Broadcoms were much more difficult to work with under Linux (although I did find that PCLinux 2007 worked &quot;out of the box&quot; with my Broadcom 4321AG if I used ndiswrapper and the Windows Vista drivers). 

Broadcom is actually one of the very few manufacturers to offer Linux support directly from their website- here is a link to download the Broadcom "STA" driver in either 32-bit or 64-bit directly from their website.  (Be sure to get the right architecture for whichever hardware you are working with though, or that will cause problems). 

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) 

I have posted on several of the Broadcom threads under Networking & Wireless sub-forum, and most of those models will work under Linux using various methods.  

Hope this helps.

Edit:  The newer Ubuntus (9.04 Jaunty Jackalope and 9.10 Karmic Koala) install that "STA" driver automatically from what I've seen, although the user must activate the driver under System>Administration>Hardware Drivers and then restart the computer.

---

