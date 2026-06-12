---
title: "WOL not working on AR8151 after upgrade to 12.04"
date: 2012-10-10
forum: Networking &amp; Wireless
---

### Post by dumb on 2012-10-10
Hi,
I've got a server with the AR8151 NIC. I was running 11.04 and had it setup with WOL, so my clients could wakeup the server, whenever they needed to. Yesterday I decided to upgrade to 12.04 (11.04 -> 11.11 -> 12.04). Everything seems to work fine, but i cannot start the server anymore, using WOL.

I've tried typing "ethtool -s eth2 wol g" and then "shutdown -h 0" but I'm unable to wake it again. This worked fine under 11.04. I'm using the kernel driver atl1c for the NIC.

Any help is appreciated.

---

### Post by arcull on 2012-10-10
Hi, don't know the exact solution, but I had similar issues. Most probably is that the NIC gets disables on shutdown, you can check this by looking at the lamp leds on the back on of NIC, if that is the case, you should prevent ubuntu from doing this, don't remember what exactly I did, but try google. If this is not case then you might try some other programs fro WOL, like ether-wake. Good luck

---

### Post by dumb on 2012-10-11
Ok, checked the /etc/default/halt config file and tried to add NETDOWN=no but it made no difference. If I only suspend the server, WOL works fine, so I'm using that as a work around for now.

---

