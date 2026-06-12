---
title: "Karmic can't connect to wireless network (USB modem)."
date: 2009-12-05
forum: Networking &amp; Wireless
---

### Post by SuperEngineer on 2009-12-05
Anyone got an idea as to how to get USB wireless modem to connect to the network (recognised & declared in wireless network list) that Jaunty has no problem with????

---

### Post by SuperEngineer on 2009-12-28
[SOLVED]

                 Workaround discussed in [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460323](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460323) has provided a fix for now but ... this issue is still a bug for correction prior to next release to maintain Ubuntu's good reputation.
 workaround details...
 Fixed with:
 Step1: add "blacklist rt2800usb" to:
           /etc/modprobe.d/blacklist.conf
Step2: add "rt2870sta" to:
           /etc/modules
Step3: Reboot.
 Connectivity now working as per Jaunty.

---

