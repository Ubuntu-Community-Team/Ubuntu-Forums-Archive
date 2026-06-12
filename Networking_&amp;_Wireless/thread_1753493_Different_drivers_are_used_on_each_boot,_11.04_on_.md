---
title: "Different drivers are used on each boot, 11.04 on Dell Inspiron N4010"
date: 2011-05-09
forum: Networking &amp; Wireless
---

### Post by GuitarzanHV on 2011-05-09
I seem to have a very weird issue.

In 10.10, my wifi worked out of the box. For 11.04, it works sometimes. If I go to a new location, I can get wireless. If I reboot there, however, its gone. Walk to another building, I'm back on. Reboot, gone. If I'm in my dorm (college student), I can get wireless by booting with the ethernet cable inserted before boot. I can't plug in the ethernet after the system is booted, though. I compared the lshw -C network commands and the nm-tool commands during the working and the non-working states, and I found something peculiar. When the wifi is working, it loads the brcm80211 driver. When its not, the driver is listed as wl. How can I get the right driver to load on boot?

Here are the two outputs for the commands:

---

### Post by GuitarzanHV on 2011-05-09
removed bcmwl-kernel-source and replaced it with the b43 fwcutter driver. Same problems as before.

Switched back to STA driver.

---

