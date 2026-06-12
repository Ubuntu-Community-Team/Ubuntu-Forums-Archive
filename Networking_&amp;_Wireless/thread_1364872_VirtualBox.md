---
title: "VirtualBox"
date: 2009-12-26
forum: Networking &amp; Wireless
---

### Post by linus2@barloon.com on 2009-12-26
I'm trying to build a Windows XP image with Ubuntu 9.04.  It installs the Windows VirtualBox, but I can't install the drivers for my Intel PRO/Wireless 2200BG.  I've downloaded the drivers from the Intel and Toshiba pages (Tablet R15-S822) and no luck with installing the drivers.  Thoughts?

---

### Post by howefield on 2009-12-26
You shouldn't need to install drivers for your guest if that is what you are trying to do. If it works in linux it should be working inside your guest.

Try watching the short videos here for more detail on how to install and create vms, then install guest additions.

[http://www.virtualbox.org/wiki/VirtualBoxTV](http://www.virtualbox.org/wiki/VirtualBoxTV)

---

### Post by impact on 2009-12-26
You do not need those drivers. The Virtual box is a virtual PC with a virtual NIC. The Windows installation doesn't see your real NIC.

---

### Post by gradinaruvasile on 2009-12-26
> **impact said:**
> You do not need those drivers. The Virtual box is a virtual PC with a virtual NIC. The Windows installation doesn't see your real NIC.

Yup, and most devices you can assign are supported by windows xp. The rest is taken care by the Guest Additions. No PCI/Integrated devices.

You can, however, use any USB (and i think serial) device seamlessly - just set up VirtualBox to use your USB devices, connect whatever you have, give that device to the VM - it will be forwarded.

---

### Post by linus2@barloon.com on 2009-12-26
So how do I get the VirtualBox to see the wireless Intel 2200BG?

---

### Post by impact on 2009-12-27
You don't. You cannot install the drivers in the virtualized Windows environment because the virtual NIC is different from your real NIC.

Virtual Box presents a virtual wired NIC (default option is the AMD PCNet FAST III) to your Windows installation. Your Windows install will connect to the internet via this virtual NIC. Virtual box then routes all traffic from this virtual NIC to your Ubuntu host and to the internet).

---

### Post by RobertSwipe on 2009-12-27
Check the settings of the virtual machine. On the Network page, make sure the network adaptor is enabled.

Some of the other settings on that page may also be worth reviewing.

---

