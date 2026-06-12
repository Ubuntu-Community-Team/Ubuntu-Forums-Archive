---
title: "Wifi card unclaimed"
date: 2009-01-20
forum: Networking &amp; Wireless
---

### Post by pestrella on 2009-01-20
I have a HP laptop

I have recently installed ubunantu in my PC. 

I use lshw -C network command to see the status of my network devices and the wireless card is unclaimed.

How can I fix this problem?

The card is AR242x 802.11abg - from atheros

Best Regards

---

### Post by bluntknife on 2009-01-21
Hi,

I have exactly the same problem. Any help or suggestions would be greatly appreciated as usual.

Thanks.

---

### Post by 2hot6ft2 on 2009-01-21
Maybe this will help.
[quote="ledenjes"]I have a Fujitsu-Siemens Amilo Pa2510 with AMD64 processor and Atheros AR5007EG wireless adapter.

I managed to get my wireless lan working by doing the following:

I downloaded and installed the following .deb files, in the following order:
1. **linux-image-2.6.27-9-generic** ([http://packages.ubuntu.com/nl/intrepid/linux-image-2.6.27-9-generic](http://packages.ubuntu.com/nl/intrepid/linux-image-2.6.27-9-generic))

2. **linux-backports-modules-2.6.27-9-generic** ([http://packages.ubuntu.com/nl/intrepid/linux-backports-modules-2.6.27-9-generic](http://packages.ubuntu.com/nl/intrepid/linux-backports-modules-2.6.27-9-generic))

3. **linux-backports-modules-intrepid-generic** ([http://packages.ubuntu.com/nl/intrepid/linux-backports-modules-intrepid-generic](http://packages.ubuntu.com/nl/intrepid/linux-backports-modules-intrepid-generic))

Then, I opened gnome-terminal and typed the following: **lspci | grep “Atheros”**

After that, I rebooted my computer. The result: wireless internet!

Hope this will help you out, too![/quote]

---

