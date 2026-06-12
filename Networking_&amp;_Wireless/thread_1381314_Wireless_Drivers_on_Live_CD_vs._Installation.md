---
title: "Wireless Drivers on Live CD vs. Installation"
date: 2010-01-14
forum: Networking &amp; Wireless
---

### Post by daniel.b.douglas on 2010-01-14
Hey all, I created a bootable USB stick with Ubuntu 9.10 on it to reinstall Ubuntu on my Dell Inspiron 1520 laptop.  It has a Broadcom 4312 Wireless card in it.  When in the LiveCD-like mode, I was able to go to System > Administration > Hardware Drivers and activate the Broadcom STA Wireless Driver, and after restarting (since the USB can save changes) the wireless worked perfectly.  However, on the actual installation on my hard drive, the Hardware Drivers screen doesn't show any drivers available for activation.

Where is the STA driver being kept on the USB stick, and how do I download and activate it?

---

### Post by daniel.b.douglas on 2010-01-14
Just tried booting up the hard disk installation again, and now the problem is slightly different.  When I open the Hardware Drivers window, the STA driver is there.  When I click "activate" it asks me for the password to override the system policy, then the window appears saying "Downloading and installing drivers...", but after that, nothing happens or changes.

---

### Post by warfacegod on 2010-01-14
Your problem *might* be that you need to enable restricted extras. Go to: System> Admin.> Software Sources> Ubuntu software tab and check multiverse. You may also want to check the Cannonical partner line under the Other Software tab. Then update.

---

