---
title: "How do I link one wireless router to another?"
date: 2011-12-26
forum: Networking &amp; Wireless
---

### Post by bwallum on 2011-12-26
Hi

I'm trying to link two wireless routers together wirelessly. Is that possible?

---

### Post by lindsay7 on 2011-12-26
Why? What are you trying to do? I would help in answering your question

---

### Post by boldford on 2011-12-26
Are you trying to create another Wifi AP to enlarge the current coverage or create a WDS?

---

### Post by bwallum on 2011-12-29
I am trying to extend the range of my network within my house (old thick stone wall type) by using the same incoming adsl service point and without using any ethernet cable.

The concept is to place a second wireless router at the 'just within but still sensible speed' limit of the primary wireless router attached to the incoming adsl broadband service. Both are Netgear wireless routers. The second router would then give coverage to a part of the house which currently cannot receive a signal from the primary router.

---

### Post by lost.soul on 2011-12-30
Your second router needs to be set as "repeater" does your netgear have this option ?

If not, might be worth looking into flashing it with DD-WRT firmware.

---

### Post by bwallum on 2011-12-30
> **lost.soul said:**
> Your second router needs to be set as "repeater" does your netgear have this option ?

If not, might be worth looking into flashing it with DD-WRT firmware.

Brilliant steer Lost-soul, thanks. 

This I found particularly useful:- [http://www.dd-wrt.com/wiki/index.php/Linking_Routers](http://www.dd-wrt.com/wiki/index.php/Linking_Routers)

My Netgear DG834PN is my primary (adsl) router, unfortunately it is a TI chipped router and there is no dd-wrt firmware for it. My extension router is a Netgear WNR834B (broadcom chipped) which does run the dd-wrt firmware. Easily flashed but sequence is important and what a revelation, I can finally see what controls I can have over the router and am now looking for a dd-wrt compatible broadcom chipped router ([http://www.dd-wrt.com/site/support/router-database](http://www.dd-wrt.com/site/support/router-database)) that I can pick up cheap to get full control of my primary router.

DD-WRT have an exhaustive wiki and a host of tutorials to really get to grips with networking.

Thank's again for the brilliant steer.

---

### Post by boldford on 2011-12-30
If you can possibly run a CAT5 cable betwixt the two you can get it up and running without the faff of flashing the router. Purely config.

---

### Post by bwallum on 2011-12-30
> **boldford said:**
> If you can possibly run a CAT5 cable betwixt the two you can get it up and running without the faff of flashing the router. Purely config.

Indeed, but I wanted to be cable free, the walls here are 30" thick and I don't like cable pinned to skirtings and architraves. The re flashing really taught me a great deal about routing as well, so I'm pleased I tried to do it wirelessly. I now know how to daisy chain wireless routers to give greater range, how to tune the network for best performance and the knowledge that piece of firmware gave me is enormous. It's amazing how much proprietory oem firmware hides the functionality of routers. dd-wrt has opened that all up for me.

I've pushed a bit further and managed to get both routers working together using a 'Repeater Bridge'. Really simple using dd-wrt. You only need dd-wrt firmware on the secondary router. The primary router, even though it was not compatible to install dd-wrt firmware, was simply accessed by the secondary router as if it were just another wireless station (e.g. a laptop). From the secondary I can run wired and wireless machines, the only constraint being the total network has to be less than 254 machines (you lose one of those slots every time you daisy chain another router too).

---

### Post by johnwags on 2011-12-31
there is complicated process to connect one wireless router to another

---

