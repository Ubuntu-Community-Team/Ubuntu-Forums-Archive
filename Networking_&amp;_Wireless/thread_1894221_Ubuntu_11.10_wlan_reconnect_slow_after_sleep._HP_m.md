---
title: "Ubuntu 11.10 wlan reconnect slow after sleep. HP mini 210."
date: 2011-12-12
forum: Networking &amp; Wireless
---

### Post by daathi on 2011-12-12
Newly installed 11.10, WLAN does connect always after sleep, but it happens quite slowly. This behaviour also happened with 11.04, but at that time I found a fix from the net, I'm not able to find it anymore. HW is HP Mini 210-1023. Has anyone faced the same problem?

---

### Post by daathi on 2011-12-14
This was it, but it doesn't seem to have any effect in 11.10: [http://askubuntu.com/questions/19171/slow-wireless-reconnect-after-suspend](http://askubuntu.com/questions/19171/slow-wireless-reconnect-after-suspend) .

If anyone knows a solution, please share! We use suspend in our mini a lot every day, so it's quite frustrating always to wait for the WLAN to connect.

---

### Post by fittzwing on 2012-09-07
I have the same problem with an HP TM 2-2150 tablet laptop and Lubuntu 12.04.  The wireless is excruciatingly slow (minutes) in reconnecting after suspend.  Editing etc/NetworkManager/NetworkManager.conf to change [ifupdown] managed=false to [ifupdown] managed=true helped speed up connection on reboot, but had no effect on coming out of suspend.  I have a Broadcom wireless card with additional driver activated.

---

