---
title: "RT2860 driver with Kernel Upgrade 3.2.0-38"
date: 2013-02-21
forum: Networking &amp; Wireless
---

### Post by azdavef on 2013-02-21
I just accepted the upgrade to kernel 3.2.0-38 and I am unable to insmod the Ralink RT2860 driver getting the error message "insmod: error inserting '/etc/Wireless/RT2860STA/rt2860sta.ko': -1 Invalid parameters" The rt2800pci driver is blacklisted by default in etc/modprobe.d/blacklist as being garbage, but it is the only one that works now on my system.  I have been through three previous kernel upgrades and have been able to restore the Ralink driver. And I agree that the rt2800pci driver is less than desirable.  I have commented the blacklist so I do not have to modprobe every time I log on. I have been trying to be a loyal supporter of Ubuntu since Feisty, but this stuff really needs to get straightened out for us regular kind of folks.  Wireless connections are really kind of important.  Does anyone have an idea about how to fix this?

---

### Post by azdavef on 2013-02-22
I removed all traces of the rt2860 driver and reinstalled it. This fixed my problem. The three previous kernel upgrades did not require me to do this.:confused:

---

