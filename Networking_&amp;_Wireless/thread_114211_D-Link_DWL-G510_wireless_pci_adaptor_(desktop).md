---
title: "D-Link DWL-G510 wireless pci adaptor (desktop)"
date: 2006-01-08
forum: Networking &amp; Wireless
---

### Post by kane_666 on 2006-01-08
hey i'm thinking of buying this card: D-Link DWL-G510 wireless pci adaptor (desktop) [HTML]http://www.dse.com.au/cgi-bin/dse.storefront/43c0cbd509a6b144273fc0a87f9c075d/Product/View/XH6312[/HTML] ive looked at ndiswrapper(is that right?) and ive found the card, but they tested it on gentoo (i think) but i was wondering if it worked on ubuntu... anyone tried? thanks

---

### Post by Lambert on 2006-01-08
Dependes on the revision as they used different chipsets in these cards. the original release and rev B1 used atheros chipset. There is a native driver in breezy for this chipset (madwifi)
Revision C1 used ralink chipset, there is also a driver inbreezy for this (rt2500)

There may be others used I didn't see with a quick search. ndiswrapper works the same on gentoo or ubuntu. 

Wireless can be tricky in any linux distro. This card will work but there's always that chance you could spend a little time configuring and tweaking the settings.

---

### Post by kane_666 on 2006-01-08
well has annyone else tried this card? or is there any one that feels like going out an buying the card and testing it for me :)

EDIT: will this card work with **any** wireless router?

---

### Post by kmacc on 2006-01-13
I've got this card: rev B1. It mostly worked right out of the box. I'm still having trouble getting it to work at boot all by itself but once I tell it, it seems pretty solid.

Cheers,

kmacc

---

### Post by rafucho on 2006-02-14
I have rev. A1, could you please help, because it didn't work out of the box, how could I install it?

---

### Post by Lambert on 2006-02-14
[quote=rafucho]I have rev. A1, could you please help, because it didn't work out of the box, how could I install it?[/quote]

let's start by posting output of these commands

sudo lshw -C network

lspci -v | grep -A 5 Eth

---

