---
title: "Wifi working... but not for Knetwork Manager"
date: 2011-06-01
forum: Networking &amp; Wireless
---

### Post by wakko_kid on 2011-06-01
Hi,
i just installed natty on my Dell Vostro 1520.
Every works fine, in particular my broadcom 4312 was detected, in fact with wi-cd i can connect to my wifi  without any problem BUT...

Knetwork Manager doesn't see the wifi interface:
Bringing up the pop-up, i can read "eth1 Unavailable",  and the check-box is grayed out (disabled).

Any idea to make Knetwork Manager work properly?

P.S.: to turn on the wifi led i can't just switch the wifi switch, but i must run "sudo ifconfig eth1 up"

Thanks to all readers,
Carlo.

---

### Post by wakko_kid on 2011-06-02
The problem was dued to the dell-laptop module.
Two wireless interfaces where foud by rfkill, one of wich always shutted down. 
Once blacklisted dell-laptop module, rfkill correctly sees only one interface and KnetworkManager works properly.

---

