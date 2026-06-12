---
title: "no wifi after resume from sleep"
date: 2006-07-08
forum: Networking &amp; Wireless
---

### Post by Doug_M on 2006-07-08
Hi, when I close the ibook it goes into sleep mode.  When I open it my network is down. During the install it offered to set up my airport "card" as eth0 which no other distro has done. They all had it as eth1. Anyway, it worked.

When I watched the console output during wakening I as that it resumed eth1 but not eth0 (airport). So I edited iftab and swapped eth0 and eth1. Then I tried waking from sleep again. This time it was eth0 that was resumed and not eth1.

So what do I need to edit to tell it to resume the airport card?

Regards,
Doug

---

