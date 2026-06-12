---
title: "Both Network Manager and WCID can't see any routers?"
date: 2012-11-24
forum: Networking &amp; Wireless
---

### Post by ikan on 2012-11-24
After installing all the updates and resetting, Network Manager and WICD can't locate any routers..
I'm running Ubuntu 12.10 alongside OSX Lion on a Macbook Air 2011.
Can't go online using Ubuntu, so I'm posting this from another PC.
Is there a way to fix this? New Ubuntu user btw, so still a noob xD

EDIT: I can't seem to "switch on Wi-Fi" on WICD too..

---

### Post by 2F4U on 2012-11-24
So just to be sure, the connection worked before the updates? Are you connecting wired or wireless and are both non-functional?

---

### Post by ikan on 2012-11-24
Yep. Worked before the update. I'm connecting using wireless, and its non-functional. No ethernet port, so can't connect wired..

---

### Post by ikan on 2012-11-25
Got it to work, guys!
If you guys had a similar problem, do what I did:
[http://askubuntu.com/questions/214156/wireless-does-not-work-anymore-after-software-update-with-ubuntu-12-10-on-a-dell](http://askubuntu.com/questions/214156/wireless-does-not-work-anymore-after-software-update-with-ubuntu-12-10-on-a-dell)
download the linux-headers-generic and bcmwl manually, and install them using Synaptic:
[http://askubuntu.com/questions/216746/dependency-not-satisfiable-offline-deb-package-install](http://askubuntu.com/questions/216746/dependency-not-satisfiable-offline-deb-package-install)

---

