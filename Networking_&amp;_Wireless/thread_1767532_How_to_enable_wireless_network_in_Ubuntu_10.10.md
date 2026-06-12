---
title: "How to enable wireless network in Ubuntu 10.10"
date: 2011-05-25
forum: Networking &amp; Wireless
---

### Post by reidun on 2011-05-25
Hi, I have an Averatec 3200 laptop with a Intel PRO/Wireless 2200BG card. When I click on Network Connections, it says wireless is disabled. I checked my /var/lib/NetworkManager/NetworkManager.state file, and it said "wireless enabled=false" so I changed it to true. It just goes back to false on reboot. I also ran rfkill unblock all, but rfkill list still shows that there is a hardware block on. The driver for this wireless card shows that it is installed. I'm not sure what to try next!

I just bought this computer used, and freshly installed Ubuntu 10.10 on it, so can't say if it worked in any other distro.

Any help would be much appreciated!

---

### Post by reidun on 2011-05-25
Solved! I googled rfkill hard block and found out that there is a button on my laptop to push to remove the hard block. Wireless now works just fine!

---

### Post by mikewhatever on 2011-05-25
Very interesting, and what was the button? Was it a dedicated wifi switch or just a keyboard combination?

---

### Post by reidun on 2011-05-25
> **mikewhatever said:**
> Very interesting, and what was the button? Was it a dedicated wifi switch or just a keyboard combination?

It is a small button right next to the power button. It has a wifi network symbol on it. Apparently it blocks the wireless card. I pressed it and rfkill list no longer shows a hard block.

---

