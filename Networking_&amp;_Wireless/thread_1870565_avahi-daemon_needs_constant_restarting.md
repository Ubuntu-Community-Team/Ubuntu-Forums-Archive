---
title: "avahi-daemon needs constant restarting"
date: 2011-10-27
forum: Networking &amp; Wireless
---

### Post by heggink on 2011-10-27
I use my ubuntu 32bit system (server kernel) as time machine backup system. It has run without any errors for years until the 11.10 upgrade: the Mac sees my box just fine ONCE but after some time it does not see any services being advertised thru avahi. Restarting avahi-daemon resolves the issue until the same happens again. I now restart avahi daemon thru cron just to be able to back up the Mac.

When the service is lost, avahi-daemon is still running and responsive (avahi-daemon -c gives 0) and no errors in the system log at all...

Any thoughts/suggestions on how to find the cause and resolve?

H:confused:

---

