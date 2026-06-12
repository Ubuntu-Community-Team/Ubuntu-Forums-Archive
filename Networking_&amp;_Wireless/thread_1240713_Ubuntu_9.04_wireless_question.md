---
title: "Ubuntu 9.04 wireless question"
date: 2009-08-15
forum: Networking &amp; Wireless
---

### Post by gobuntu on 2009-08-15
Dear forum people,

I tried the Live CD of Ubuntu 9.04 and I can not connect wirelessly to the web. This HP laptop has the wireless chipset Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02).

I have been told that that chip does not work "out of the box".

So, if I do permanent install Ubuntu 9.04 i386, what will I have to do to implement wireless?

Thanks!

---

### Post by MaindotC on 2009-08-15
You need to have a wired connection, and at the top there will be an icon that says "Restricted Drivers Manager".  When you start that, it will allow you the option to enable the Broadcom drivers.  When you do, it will automatically download and install them.  I bet dimes to donuts you'll have to do a lot more than that but that will get you off to a good start.

---

### Post by gobuntu on 2009-08-15
> **strAlan said:**
> You need to have a wired connection, and at the top there will be an icon that says "Restricted Drivers Manager".  When you start that, it will allow you the option to enable the Broadcom drivers.  When you do, it will automatically download and install them.  I bet dimes to donuts you'll have to do a lot more than that but that will get you off to a good start.

Thank you StrAlan.

Does your reply mean that now there's no need for ndiswrapper, but just merely using proprietary drivers will do?

Also, will using the Broadcom proprietary be better than ndiswrapper?

Reason for my questions, is I want to install the most functional and robust, option, even if one is more work than the other.

Thanks!

---

### Post by MaindotC on 2009-08-15
It depends - no one can say for certain something works better than something else without having tested it in the very specific conditions you describe.  You can use the proprietary driver, or you can use ndis.

---

### Post by gobuntu on 2009-08-15
> **strAlan said:**
> It depends - no one can say for certain something works better than something else without having tested it in the very specific conditions you describe.  You can use the proprietary driver, or you can use ndis.

Thanks strAlan. Will try the prop first and see how it does. If not will do ndis.

---

