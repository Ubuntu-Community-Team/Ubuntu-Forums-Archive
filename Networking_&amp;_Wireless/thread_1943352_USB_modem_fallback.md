---
title: "USB modem fallback?"
date: 2012-03-19
forum: Networking &amp; Wireless
---

### Post by Fafler on 2012-03-19
Hi. I've been searching for a tutorial for using a USB GSM modem as fallback for my DSL connection on my home server/router, but i can't seem to find anything.

I guess have do make a cron script that run every that often that pings a known outside ip, and if it's unreachable, opens the ppp connection and reconfigures the iptables rules to route through the USB modem. Then it has to watch the DSL and reverse the settings when it comes back up. Is that correct? Is there a easier way to do it?

---

