---
title: "Issues with removing /etc/udev/rules/70-persistent-networking.rules?"
date: 2012-09-25
forum: Networking &amp; Wireless
---

### Post by StickyC on 2012-09-25
I'm assembling an Ubuntu 12.04 desktop disk image that will be used as a master disk image to be deployed on several identical PCs with built in wired/wireless networking.

Since each target PC will have different MAC addresses for the wired and wireless cards, that breaks the current contents of /etc/udev/rules.d/70-persistant-networking.rules which has the MAC addresses specific to the machine I'm building the master on.

I've noticed that if I delete this file, it's re-created during boot and things appear to be fine. Are there any gotchas with not including this file on the master disk image (assuming all target hardware is identical)?

Thanks!

---

### Post by diesch on 2012-09-25
No, remove all */etc/udev/rules/*persistent*.rules* on your master image so on the target machines new ones get created that match the actual hardware.

---

