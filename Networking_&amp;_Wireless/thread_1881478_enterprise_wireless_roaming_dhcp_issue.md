---
title: "enterprise wireless roaming dhcp issue"
date: 2011-11-15
forum: Networking &amp; Wireless
---

### Post by miatawnt2b on 2011-11-15
I am having a problem with our enterprise wireless environment.  Our building is very hot when it comes to signal, and even when sitting at my desk, sometimes the supplicant will roam between AP's.  We have "DHCP required" turned on.  So the problem I am having is that when I roam AP's, the supplicant will not re-request DHCP, so I can't get onto the network.  I am running the latest broadcom wl.ko driver, and a fairly stock Maverick install with networkmanager.

Any ideas on how to fix this issue?

-J

---

### Post by jonobr on 2011-11-15
Just curious,
are you using the 802.11r standard on the APs?

---

### Post by miatawnt2b on 2011-11-16
> **jonobr said:**
> Just curious,
are you using the 802.11r standard on the APs?

Negative on the 802.11r

---

### Post by jonobr on 2011-11-16
Then (stupid question from me) are you sure your switching APs and not staying on the old one?

---

### Post by miatawnt2b on 2011-11-16
positive. I re-associate with a different MAC address.
-J

---

