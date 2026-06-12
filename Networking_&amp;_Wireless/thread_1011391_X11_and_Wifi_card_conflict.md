---
title: "X11 and Wifi card conflict"
date: 2008-12-14
forum: Networking &amp; Wireless
---

### Post by computerwiz3491 on 2008-12-14
I am running Ubuntu 8.10 on a Dell Optiplex GX240. I tried installing a Trendnet TEW-421 Wifi Card into the PCI Slot. When the card is inserted, the computer seems to boot and then completely hard freezes when it attempts to load X11. 

When I remove the wifi card, everything boots and the computer works fine, but when I put it back in the computer won't boot. 

When X11 freezes, even the CAPS and NUMLOCK lights don't work on the keyboard.

I deleted the /var/log directory, and made a new one, and saved all of the new logs. I went though them and didn't see any obvious errors. The Xorg.0.log contains hardware specific stuff, but I wasn't even sure where to look, but it appeared that there were no problems.

I tried moving the card to another slot and cleaning out the slots, but same problem.

If anyone has any advice, please let me know.

Thanks.

---

