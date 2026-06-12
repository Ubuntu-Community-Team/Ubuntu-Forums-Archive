---
title: "What is the difference between ipw and wext? (AKA WPA now working with ipw2200)"
date: 2006-07-16
forum: Networking &amp; Wireless
---

### Post by vayu on 2006-07-16
dist-upgrading from Breezy to Dapper killed WPA on my laptop.  The wireless itself worked unsecured but WPA did not.

After pouring through post after post I found several different ideas, none of them particularly appealing.  Network manager didn't seem like it would work because I'm using static IP and there were references to it only working for DHCP. Plus I wanted to know how to set it up myself.

Of all the posts there were two references to using wext. It made no sense to me.  dmesg and lsmod both show ipw2200. 

Since it required changing only 4 characters in my wireless script I tried replacing ipw with wext in my call to wpa_supplicant.

It worked. Nothing else was changed. I would like to understand why.

---

