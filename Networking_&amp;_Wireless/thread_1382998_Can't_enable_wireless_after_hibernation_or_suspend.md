---
title: "Can't enable wireless after hibernation or suspend"
date: 2010-01-16
forum: Networking &amp; Wireless
---

### Post by wolfcamp on 2010-01-16
Running Ubuntu 9.10 on Dell Inspiron 6000 laptop.
When returning from hibernation or suspend, "Enable Wireless" is not available to be checked in Network Manager Applet.  A reboot is required to get my wireless working again.
How do I enable my wireless without rebooting?

---

### Post by jeffzz on 2010-01-16
Hey,

First off I am not an expert of ubuntu but I recently did some research about wireless under ubuntu 9.10. My laptop has an Atheros AR5212 chip and I had similar problems.

Try the following:
1. Restart networking
command: sudo service networking restart
2. Restart network-manager
command: sudo service network-manager restart
3. Reset your wifi
command: sudo ifconfig athx up/down
sudo ifconfig wifix up/down
4. You can restart dbus but that's not really different than reboot.

try the above and wish you luck.

> **wolfcamp said:**
> Running Ubuntu 9.10 on Dell Inspiron 6000 laptop.
When returning from hibernation or suspend, "Enable Wireless" is not available to be checked in Network Manager Applet.  A reboot is required to get my wireless working again.
How do I enable my wireless without rebooting?

---

