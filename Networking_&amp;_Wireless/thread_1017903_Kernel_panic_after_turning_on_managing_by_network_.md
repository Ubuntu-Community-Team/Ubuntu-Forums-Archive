---
title: "Kernel panic after turning on managing by network manager"
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by g0nzo on 2008-12-21
Hi,

after upgrading Ubuntu to 8.10 I had few problems: wireless network stopped working; network manager icon disappeared from notification area ; booting time takes about 2 minutes and I have to manually run "service networking restart" to turn on network after system start.

I fixed networking problem by using wired network. The network manager icon fixed itself with the recent updates.

However, after clicking on the nm icon, I get "device is unmanaged" for both wired and wireless. I've searched the forum and found simple answer to set "managed=true" in /etc/NetworkManager/nm-system-settings.conf.

Changing this value fixed the booting time and I got network on right after the system start, but the whole system halts after about 15-30 seconds and Caps Lock and Scroll Lock leds are blinking on the keyboard. After searching the forum again, I've found that it means "kernel panic" and installing linux-backports-modules-intrepid package is supposed to fix it, because of some bug in intel wireless driver. The problem is that I don't have intel card, but something like:
Texas Instruments ACX 111 54Mbps Wireless Interface
and I still got this problem after installing the package.

Any ideas how to fix it?

---

