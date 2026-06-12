---
title: "Safecom SWLUT-54125 not working"
date: 2010-05-27
forum: Networking &amp; Wireless
---

### Post by BorgCymru on 2010-05-27
running lsusb I get

Bus 001 Device 005: ID 07b8:b21a D-Link Corp. 802.11g wireless Adaptor

But I can't find the adaptor in any of the network connections or settings.


Anyone help please

---

### Post by chili555 on 2010-05-27
This was previously driven by the flaky, poor module *acx*. It has been removed from the kernel. ndiswrapper is the accepted method to get it working. Do you have the driver CD that came with the device? I believe you need the XP inf and maybe sys files.

---

### Post by BorgCymru on 2010-05-27
yep got the CD

---

### Post by chili555 on 2010-05-27
I suggest you right-click your desktop and create a folder. I suggest calling it safecom. Now browse the CD and find the XP drivers and drag and drop the .inf and .sys files to the folder safecom.

Now open System > Administration > Windows Wireless Drivers and click Install New Driver. Navigate to the .inf file at Desktop > safecom and install it. You should be all set.

Post back with any questions.

---

