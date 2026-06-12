---
title: "Wireless networking waiting for ip address"
date: 2013-04-27
forum: Networking &amp; Wireless
---

### Post by jeppebundsgaard on 2013-04-27
Hello,
Upon upgrading to Raring on my Lenovo E135 the wireless is not working. It did before. The network manager tells me that it is connected and waits for an ip address. It never gets one, and after some time it asks for credentials. I know they were right in the first place.

I have tried to uninstall network manager and reinstall it (by mistake I also tried Gnome Network manager).
Wired network works fine.
The wireless netcard is eth1 (using driver wl), the wired is eth0. I guess that doesn't matter?

Any suggestions?

Best regards,
Jeppe

---

### Post by jeppebundsgaard on 2013-04-27
I found out from here: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) that I must have had the proprietary driver [bcmwl-kernel-source]("https://launchpad.net/ubuntu/+source/bcmwl") installed for my Broadcom 4313. I tried to reinstall, it didn't help. I then uninstalled it because I read that the open source driver [brcmsmac]("http://wireless.kernel.org/en/users/Drivers/brcm80211") was integrated into the kernel. Now the network is connected!

---

