---
title: "Either Samba, Apache 2, Printer service (cupsys) or ssh server affect wireless"
date: 2006-06-25
forum: Networking &amp; Wireless
---

### Post by leo_m on 2006-06-25
I removed the above-mentioned from start up services (System|Administration|Services) and the wireless started working again (after a reboot).

Prior to that, I had done some updates and additions to my packages from the ubuntu universe (unsupported package space).

The problem was that ipw2200 could not load the firmware although it was there in the folders (the driver said it could not load firmware).

Once the above services were removed from the startup services, things returned to normal.

This is just for information and if someone experiences similar problem, kindly post it here.

Will explore later exactly which service causes the problem.

---

### Post by sade on 2006-09-25
Hi,

I have the same problem with the ipw2200 driver (v 1.2.0). I installed the appropriate network stack and copied the firmware files to /usr/lib/hotplug/firmware, but I get "could not load firmware" error message at system startup. Is there another way to fix the problem, besides removing the services, since I want to use them?

Regards,
Isabella

---

