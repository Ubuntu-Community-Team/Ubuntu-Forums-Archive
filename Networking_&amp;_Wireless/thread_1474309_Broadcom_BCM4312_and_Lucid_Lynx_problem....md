---
title: "Broadcom BCM4312 and Lucid Lynx problem..."
date: 2010-05-05
forum: Networking &amp; Wireless
---

### Post by rmflagg on 2010-05-05
Hi all,
   I have a Dell Mini 9, with a Broadcom BCM4312, 14e4:4315, wireless card.

   I cannot get it to show any networks and I have tried everything I can find to get it fixed, but with no luck.

   I have reinstalled bcmwl-kernel-source and everything else, but nothing works.

   Has anyone else had this problem and what solution(if any) have you found for it?

Thanks in advance!

---

### Post by Jim_in_Omaha on 2010-05-06
Here is a post I made earlier with some wireless Broadcom issues on a Dell D6400. Perhaps it will help you.

[http://ubuntuforums.org/showthread.php?t=1473579]("http://ubuntuforums.org/showthread.php?t=1473579")

---

### Post by walker98t on 2010-05-13
Don't know if this will help or not, but I had the same problem on my Mini9. Couldn't get it to display any wireless networks at all. After trying several things I found in different forums, I stumbled across the solution... and felt like an idiot for not seeing it sooner. I'm using wicd to connect, and the wired interface was listed as eth0; the wireless interface was listed as wlan. I changed "wlan" to "eth1", and immediately had working wireless.

If you have tried installing different drivers, make sure you have the correct one installed. In Synaptic, do a search for "broadcom". Reinstall two packages: bcmwl-kernel-source and bcmwl-modaliases. If you have any of the others installed, uninstall them.

Hope this helps.

---

