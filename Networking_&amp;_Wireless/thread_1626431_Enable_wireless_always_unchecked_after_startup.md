---
title: "Enable wireless always unchecked after startup"
date: 2010-11-20
forum: Networking &amp; Wireless
---

### Post by RBLevin on 2010-11-20
Greetings. On my Lenovo IdeaPad S12, the "Enable wireless" checkbox is always unchecked after startup. After I check it, it automatically connects to the preferred wireless network. Is there a way to ensure that wireless is always enabled after startup? On my other PCs, "enable wireless" remains set properly after startup. It's only on my Lenovo that I have noticed this problem. I have poked through the various network tools to see if there's a preference setting for this, and have not found one. Thanks.

---

### Post by Forte125 on 2010-11-30
Several other people are having the same problem,  but I have derived a workaround.

Try this first (It works for most people):

sudo rfkill unblock wifi

If that does not work (It didn't for me) try what's listed below:


1. Open up software center
2. Download Wicd
3. Go to System -> Preferences -> Startup Applications
4. Disable network manager at startup
5. Reconfigure your network in Wicd
6. restart


There were some other ideas as to how to fix it being discussed on [this thread]("http://ubuntuforums.org/showthread.php?t=1596043&page=4").

Good luck and report back if it does/does not work.

Just an FYI, I think this issue pertains to Lenovo laptops with a Broadcom Wireless card (I am using a Lenovo V460)

:)

---

### Post by RBLevin on 2010-11-30
Hey, thanks. I'll try that.

---

