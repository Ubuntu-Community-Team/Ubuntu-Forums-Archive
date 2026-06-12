---
title: "dhclient causes crash - why?"
date: 2005-03-14
forum: Networking &amp; Wireless
---

### Post by fritzk3 on 2005-03-14
I am using Hoary and trying to get my DWL-G510 wireless card working.

I am able to load the driver with ndiswrapper, and set the WEP key.  If I do "iwconfig wlan0" everything looks fine.  So, the next step is to do dhclient - which spits out a bunch of status messages, but eventually something that looks like success.

The next thing I do is switch to Firefox and try to type a URL.  Nope.  Ubuntu CRASHES.  Totally.  Completely.  Cursor frozen.  No response to anything but the power button.

Any idea WHY this is happening after I issue the dhclient command?

---

### Post by alastair on 2005-03-14
No idea. But ndiswrapper might be the culprit. It might be that NOT doing dhclient and doing some things with the computer (after loading the wireless) might cause the problem. Worth checking.

Post some logs :

/var/log/syslog

from wireless driver load, dhclient messages to any crash messages. See if there are any errors.

---

