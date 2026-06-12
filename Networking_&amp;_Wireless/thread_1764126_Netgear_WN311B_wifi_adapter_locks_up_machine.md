---
title: "Netgear WN311B wifi adapter locks up machine"
date: 2011-05-21
forum: Networking &amp; Wireless
---

### Post by NGunslinger on 2011-05-21
I have a Netgear WN311B wifi adapter that worked fine under Ubuntu 10.10. After installing 11.04, my machine locked up whenever I tried to transfer more than a few kB over wifi (e.g. - the home page for my web browser loaded fine but if I tried to do a speed test, it would freeze up the whole machine after about 5 seconds).

I moved the machine downstairs so that I could use a wired connection to my router and also did a clean install of 11.04 to isolate the problem. The machine worked fine as long as it was connected via the ethernet adapter, but when I tried to use the wifi it froze again, with the exception that this time the screen went into text mode and output the following over and over:

[435.610002] ehci_hcd 0000:00:13.2: PCI-DMA: Out of IOMMU space for 18 bytes

I'm at a loss here. I can't seem to find any threads on similar problems in the forums.

---

### Post by uhurusurfa on 2011-06-10
I have just started experiencing the same problem after upgrading from 2GB to 4GB RAM on AMD64 Dell Inspiron - takes a few minutes and then the IOMMU errors start appearing. Prior to that the system was stable.

I have a B4311 Broadcom wireless device using the 10.04 driver since the 11.04 driver did not work.

---

### Post by uhurusurfa on 2011-06-11
I uninstalled the Broadcom provided driver from 10.04 and used the firmware-b43-installer and fw-cutter (removed the blacklist items for b43 in /etc/modprobe.d/broadcom-sta-common.conf) per [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx).

So far the system seems stable so am assuming it was the old driver creating IOMMU problems.

---

### Post by ravensqu on 2011-08-13
I am also attempting to use a WN311B in ubuntu 11.04 x64 and have tried following the without internet access instructions for installing the b43 drivers. After following all the steps though, the drivers are not appearing in the list of additional drivers. I followed all the steps exacly but the b43 drivers just didn't show up.

---

