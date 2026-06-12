---
title: "Realtek wireless disabled on Ubuntu 11.04 x64"
date: 2011-05-30
forum: Networking &amp; Wireless
---

### Post by pythonscript on 2011-05-30
I have a Thinkpad with a Realtek RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01) embedded wireless chip. I've been having connection problems (see this thread: [http://ubuntuforums.org/showthread.php?t=1769743](http://ubuntuforums.org/showthread.php?t=1769743)) that, as of now, make the computer practically unusable as a portable machine.

I downloaded the newest driver from the Realtek website and installed it, which broke the system and required chrooting into it from a live CD to uninstall the driver (that's from this thread: [http://ubuntuforums.org/showthread.php?t=1771442](http://ubuntuforums.org/showthread.php?t=1771442)). I successfully uninstalled the driver from a live CD, but now, wireless is missing when I boot into the working system. I ran:

```
lspci -k
``` and this is the result: 
> 05:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device 8195
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
    Subsystem: Lenovo Device 2131
    Kernel driver in use: r8169
    Kernel modules: r8169I included the Realtek ethernet controller, in case it helps. I saw it mentioned in another thread as potentially useful, so here's the output from lspci -nn as well:

> 05:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)There aren't any Realtek modules in /etc/modprobe.d/blacklist.conf, but I don't know which module I need to load to get the wireless working again. I know it certainly *isn't* the one from Realtek's website. 

EDIT: I also know from this thread ([http://ubuntuforums.org/showthread.php?t=1770202](http://ubuntuforums.org/showthread.php?t=1770202)) that someone else is having a different but equally frustrating problem with the same Realtek wireless chip that I have, and I've read that the kernel support for these chips is weak throughout kernel v2.6.38. 

Thank you for the help!

---

