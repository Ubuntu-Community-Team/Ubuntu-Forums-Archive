---
title: "No wireless networks found after a while"
date: 2010-09-05
forum: Networking &amp; Wireless
---

### Post by thayes on 2010-09-05
I'm running Ubuntu 10.04 64bit on a Thinkpad T61, and I keep running into some issues with the wireless networks. For a while, the connection works fine (sometimes several hours, sometimes 15 minutes or so--there doesn't appear to be an event associated with it). Eventually, though, the connection disappears; first, though the widgets say I'm connected, nothing will go through, and soon after, it realizes I'm not connected and, moreover, it can't find a single wireless network, despite the fact that it was just fine a couple of minutes beforehand (and other devices still have access to the WLAN, so I know that the router hasn't crapped out). I've tried using wicd, but the same thing happens. Any idea what could be the cause?

---

### Post by DjSesso on 2010-09-05
Is it a broadcom card? I had the same issue on my dell. It fixed itself after doing the upgrade to the Network Manager. I also changed to the "wl" driver.

---

### Post by thayes on 2010-09-19
I don't know if it's a Broadcom card (it's an Intel Wireless WiFi Link 4965AGN), but I seem to have resolved the problem. I had both Network Manager and Wicd installed, and I guess they weren't playing nicely together. I uninstalled Network Manager, and so far, everything seems to be gravy. Only time will tell for sure, though.

---

