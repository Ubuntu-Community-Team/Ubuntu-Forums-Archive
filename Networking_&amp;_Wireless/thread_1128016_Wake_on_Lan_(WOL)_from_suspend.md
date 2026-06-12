---
title: "Wake on Lan (WOL) from suspend"
date: 2009-04-17
forum: Networking &amp; Wireless
---

### Post by jmcarter on 2009-04-17
Hi,

I have been attempting to get WOL working when the pc is in a suspended state under Hardy 8.04. The network card is integrated with the motherboard (Marvell Yukon 88E8001). I have got the computer waking from a turned off state fairly easily, but it refuses to wake from a suspended or hibernated state.  I have made numerous changes, from making changes in the /proc/acpi/wakeup to installing the sk98lin (from the Marvell wesbite) in place of the default skge driver, with no success.

Whichever state the computer is in, be it turned off, hibernated or suspended, the LED on the router indicating a connection with the computer is always on, so I believe the network card is still active.

Is this an issue with the driver for the network card, or am I missing something else?  I've been through a large number of posts on this forum, and none of the recommendations seem to work for me, and now feel it's becoming a lost cause.

I see quite a few people have WOL working from suspend but not from a turned off state. oh how I envy you ;)

Thanks in advance for any help,

Jacob

---

