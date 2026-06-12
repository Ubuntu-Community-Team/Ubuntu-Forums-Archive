---
title: "No Wireless with Reinstall. Please Help!!"
date: 2010-11-17
forum: Networking &amp; Wireless
---

### Post by kiki298 on 2010-11-17
Some of you may have seen my post about my wireless issues. I gave up trying to figure out the problem and just reinstalled 10.10. Anyways, did the reinstall, installed all proprietary drivers and STILL NO WIRELESS. Seriously, what the heck is going on? I'm getting really frustrated and would like any help I could get :)

Again, computer is HP Pavillion dv2500, using 10.10, and the wireless driver is the Broadcom 802.11 Linux STA wireless driver. 

I previously had access to the Internet, so I really don't know what could have changed.

---

### Post by kiki298 on 2010-11-17
I fixed it :D

> **Forte125 said:**
> I think I found a solution:
 
 sudo rfkill unblock wifi

Did that, my wireless light came on right away, but I had to restart  before I could use the wireless card. Just posting this so others who find this thread get a solution :).

---

