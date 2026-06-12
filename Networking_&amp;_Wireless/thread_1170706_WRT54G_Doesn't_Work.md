---
title: "WRT54G Doesn't Work?"
date: 2009-05-26
forum: Networking &amp; Wireless
---

### Post by snowman4839 on 2009-05-26
I don't understand why but my Atheros ar5007eg (i think) on my Asus 900HA doesn't work at all with the standard drivers from 9.04 when I try to use it with my Linksys WRT54G router but it works fine with another router. I tried using it with Madwifi but the ones built into 9.04 doesn't work. But I used madwifi-trunk-r4023-20090520 and installed that and now it works somewhat with my WRT54G and still works fantastically with the other router. Now I just don't get why it doesn't work for crap when I try to use it with the WRT54G but other routers it is fine. Now I was hoping to find a solution or a reason why this doesn't work with my WRT54. Thanks.

---

### Post by thesavager on 2009-05-26
Hi,

I had the same problem, and figured out that the problem was the wpa2 encryption,on the WRT54G router.
I switched to wpa and everything runs great again.
Somehow the wpa2 encryption is broken in the WRT54 series.

Savager

---

### Post by snowman4839 on 2009-05-26
Well actually it doesn't have any encryption on it at all. I was thinking about putting DD-WRT on it. Think that will help?

---

### Post by dmizer on 2009-05-26
> **snowman4839 said:**
> Well actually it doesn't have any encryption on it at all. I was thinking about putting DD-WRT on it. Think that will help?

Since you say it works fine with other routers, this may be a good solution for you.

---

### Post by PGHammer on 2009-05-26
> **snowman4839 said:**
> Well actually it doesn't have any encryption on it at all. I was thinking about putting DD-WRT on it. Think that will help?

DD-WRT is one of the better third-party firmware solutions for Linksys routers (I have it on my WRT54GS, which is the MIMO-G version of the 54G).  It (DD-WRT) supports both WPA and WPA2 (though I normally use WPA with the GS, as it supports a laptop running XP Professional, which has issues with WPA2, as opposed to my dual-boot Jaunty/Windows 7 desktop, which is now unwired to the same router).  The desktop, unlike the laptop, goes nowhere (and is right next to the router).  Yes; the desktop would normally be *wired*; however, because I was able to finally get a CardBus G card for the laptop, I have the laptop's old USB G adapter connected to my desktop for testing.

---

