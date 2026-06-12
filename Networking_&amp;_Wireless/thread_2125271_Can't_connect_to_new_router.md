---
title: "Can't connect to new router"
date: 2013-03-13
forum: Networking &amp; Wireless
---

### Post by Corfy on 2013-03-13
I'm having a weird problem. A power surge/outage knocked out my home router, so I went out and bought a new one (that's not my problem). But now, my Ubuntu laptop won't connect to the new router (it will see it, and many others, when I pull up a list of available wireless networks, but it will not connect). My computer connected fine with the previous router, and my wife's Ubuntu laptop connects to the new router just fine (as does Windows on both our computers - both our laptops are dual-boot - and our Android phones connect fine as well). 

I had this problem once before a long time ago when switching routers, and solved it by deleting the Wireless network entry for that SSID on my laptop and recreating it. That hasn't helped this time, though.

It occurred to me that there might be some settings buried somewhere in the system that might be causing a conflict that aren't getting deleted, but I don't know where else to look. I don't have any idea what else the problem could be. I also can't tell what the problem is that is preventing my computer to connect. All I can say is it tries for about 30 seconds to connect, and then pops up a message that the wireless is disconnected, and after a few seconds, it will try again, and it will just repeat that until I tell it to stop. 

If it matters, I'm running Ubuntu 12.10 64-bit (upgraded from 12.04, if that matters), but then, I was before I switched routers, too. The wireless network is encrypted with WPA2 personal, which I haven't had a problem with before. Also if it matters, my new router is a Netgear N600 (WNDR3400v2).

---

### Post by steeldriver on 2013-03-13
Is the new router wireless-n and the old one was wireless-g perhaps? that might cause problems if the adapter is now trying to connect at n-rates (some Intel adapters in particular seem to have probelms with n)

In any case, you could look at dmesg for network adapter related stuff e.g.

```
dmesg | grep -Ew 'eth[0-9]|wlan[0-9]'
```

(you may need to change the eth or wlan parts depending on how your network devices are named)

---

### Post by Corfy on 2013-03-13
(Sorry it took so long to get back with you... got pulled away with other things)

Yes, it is an N router (or at least, N capable), but I'm pretty sure I don't have an N wireless card. But if something in my system is trying to connect as N, I don't know how to change it.

I ran the command you suggested, and came up with this result: 

[   21.230800] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 6.20.155.1 (r326264)

---

### Post by Corfy on 2013-03-13
I do owe you my thanks. I wasn't previously aware there was a problem with "N" routers, and I didn't stumble across that with my searches. But after your comment, I searched more specifically for that, and found the answer.

The fix seemed to be to go to "Software Sources" (either through the Software Center or Synaptic), go to the "Other Drivers" tab, de-select the driver, apply, re-select the driver, apply again, and then restart the computer (or, alternatively, restart the networking, but as I had to step away from the computer anyway, a restart seemed to make as much sense). I am now typing this from my Ubuntu laptop using the wireless connection.

---

### Post by steeldriver on 2013-03-13
OK that's great - I wasn't actually aware that particular Broadcom device had a similar issue OR that there was an available driver fix for it - glad you figured it out

---

### Post by Corfy on 2013-03-13
I don't particuarly understand why the fix worked. Basically, all it was involved disabling the driver and then re-enabling, which I would have expected a computer reboot would do. I didn't have to download a new driver or reinstall the existing driver. It seemed more like a Windows fix rather than a Linux fix.

---

