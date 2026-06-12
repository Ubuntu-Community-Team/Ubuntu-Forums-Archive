---
title: "Problems getting Belkin f5d7001 to work"
date: 2006-06-01
forum: Networking &amp; Wireless
---

### Post by whirlibulf on 2006-06-01
Hey, I'm pretty new to linux, and so far ubuntu seems very nice ;)

The main problem I'm having at the moment is the inability to get my wireless card (Belkin f5d7001) to work. I've found it has a Broadcom 4306 chip (or something of that nature) inside, and I've heard this is natively supported in Dapper.

When I turn on my computer in windows XP, the lights on the wireless card come on about halfway through the windows boot process, but in Ubuntu, they do not seem to come on at all, even after Ubuntu has booted fully.

I can see "Wireless Connection" on eth0 in the networking manager (I think?) But it is deactivitated. When I click activate, it takes about 3 minutes before the "Activating" message goes away, and then it says "Activated" next to wireless connection, but the lights are still off, and I cannot access any network. When I close the networking manager and open it up again, it says it's deactivated again.

I'm able to see it in the list of devices ("sudo lshw" I think?,) but above it the terminal says something like " -*network DISABLED "

Any help would be appreciated, thanks :)

---

