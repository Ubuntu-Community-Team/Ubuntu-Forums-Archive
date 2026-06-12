---
title: "Some websites won't load"
date: 2009-11-24
forum: Networking &amp; Wireless
---

### Post by Sardien on 2009-11-24
Hi all,

Got quite a strange problem.

Running Ubuntu 9.04 on a laptop that connects to iBurst ([Wireless Broadband]("https://help.ubuntu.com/community/MobileWirelessBroadband")) over PPPoE (using the UTD modem).

For some reason a few websites will not load. So far the only two I know of are dailymail.co.uk and huffingtonpost.com (I haven't tested extensively). It resolves the domains fine, but just sits loading a blank page forever.

I've tried both FireFox and Chromium, same result.

If I connect via PPPoE to DSL they work fine. If I connect over WiFi to DSL they work fine. If I connect to iBurst over PPPoE on a Vista machine the sites work fine.

Any idea as to what the problem could be?


Tried to fix the problem by upgrading to 9.10 but it does not boot on the machine ATM (seems to be buggy acpi or something).

Thanks!

Richard  :)

---

### Post by lisati on 2009-11-24
I occasionally run into sites which don't display properly, even if they've loaded properly before. Sometimes reloading the web page seems to do the trick.

---

### Post by Sardien on 2009-11-26
> **lisati said:**
> I occasionally run into sites which don't display properly, even if they've loaded properly before. Sometimes reloading the web page seems to do the trick.

Thanks for the reply lisati. Unfortunately reloading the page does not help :(

---

### Post by Sardien on 2009-12-31
Turned out to be a problem with the MTU size. I had to set it to 1392.

It took me a few hours of googling and trying different things to get the MTU set to 1392 permanently.

Setting it for the connection under "Wired Settings" in Network Manager did NOT change it!

In the end, the instructions in [this post]("http://ubuntuforums.org/showpost.php?p=7603725&postcount=5") worked. The MTU for ppp0 is now always set to 1392.

---

