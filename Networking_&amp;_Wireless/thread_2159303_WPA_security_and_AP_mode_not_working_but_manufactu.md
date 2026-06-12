---
title: "WPA security and AP mode not working but manufacturer's site says it does"
date: 2013-07-02
forum: Networking &amp; Wireless
---

### Post by mattyhatty on 2013-07-02
Hi ,
       I have a Ubuntu 12.04 on laptop with Intel PRO/Wireless 3945ABG wireless card (details from lshw).

Intel website states that WPA is supported as well as Infrastructure mode.[here]("http://www.intel.com/content/www/us/en/wireless-products/pro-wireless-3945abg-network-connection-brief.html?wapkw=intel%C2%AE+pro%2fwireless+3945abg+")

While[ here]("http://wireless.kernel.org/en/users/Drivers/iwlegacy") on linux drivers page it only supports ad-hoc.
From : iw list     Supported interface modes:
                      * IBSS
                      * managed
                      * monitor
I believed wieless cards after 2003 supported WPA and WPA2 
Is this a driver problem on linux?Does my card support WPA and AP or not?

---

### Post by praseodym on 2013-07-02
Yes, it does. "managed" is the regular infrastructure mode

---

### Post by mattyhatty on 2013-07-03
I would like to create a wifi hotspot for which I need Master(AP) mode.Managed mode makes it work as a client.I don't think my card supports it but I wanted to make sure if it's not a driver problem.Even WPA is not supported.

---

