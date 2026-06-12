---
title: "zd7000 wireless cannot get IP address"
date: 2009-10-14
forum: Networking &amp; Wireless
---

### Post by sjprice on 2009-10-14
So this old laptop is now my daughters running Edbuntu on top of 9.04. Using the Broadcom B43 legacy wireless driver (Internal card is a B4303), I can see my network, and Wicd can validate the password, but it always fails with Unable to get IP address.

I have turned off security to test, I have 20 IPs in the DHCP pool, it connects fine on the wired network...

Ideas?

---

### Post by admelfo on 2009-10-14
No expert here -- but I have come to understand that getting wireless working on older hardware is a bit of a black art, at best. (I'm running on a circa-1999 Compaq Armada M300 olaptop.)

I haven't used wicd. Have you tried madwifi? In the end, it always ends up working. Good luck!

---

### Post by admelfo on 2009-10-14
No expert here -- but I have come to understand that getting wireless working on older hardware is a bit of a black art, at best. (I'm running on a circa-1999 Compaq Armada M300 laptop.)

I haven't used wicd. Have you tried madwifi? In the end, it always ends up working. Good luck!

---

### Post by sjprice on 2009-10-15
Madwifi seems to be for Atheros chipsets, this is a Broadcom. Thanks for the input though.

Is there a log file I can tail out to see why its not getting an IP?

---

