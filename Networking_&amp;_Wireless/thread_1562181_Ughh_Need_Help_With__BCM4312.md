---
title: "Ughh Need Help With  BCM4312"
date: 2010-08-27
forum: Networking &amp; Wireless
---

### Post by Sobezilla on 2010-08-27
So I just recently migrated from Vista to Linux, I'm running Ubuntu Studio 10.04 on a HP Pavilion DV6700 with a Broadcom BCM 4312 b/g frequencies wifi adapter. I followed one guide telling me to use the hardware drivers program to activate Broadcom STA wireless driver, but whenever i attempt to do so it says "SystemError: InstallArchives() failed". Can anyone help?? (BTW i am not that adept with the Linux operating as of yet)

---

### Post by bkratz on 2010-08-27
> **Sobezilla said:**
> So I just recently migrated from Vista to Linux, I'm running Ubuntu Studio 10.04 on a HP Pavilion DV6700 with a Broadcom BCM 4312 b/g frequencies wifi adapter. I followed one guide telling me to use the hardware drivers program to activate Broadcom STA wireless driver, but whenever i attempt to do so it says "SystemError: InstallArchives() failed". Can anyone help?? (BTW i am not that adept with the Linux operating as of yet)

You do need an active wired connection when you activate the driver, do you have one?

---

### Post by halj32 on 2010-08-27
all the drivers you need are on the CD under pool restricted 
installing dkms, fakeroot, patch, and then the bcmwl-kernel-source package from the live-cd

---

### Post by Sobezilla on 2010-08-27
Yes, I'm currently connected to my router via Ethernet cable. I installed Ubuntu Studio off of the alternate install disk, I'm assuming that is different from the live disk? In wifi-radar it reads my device as being there (i have read that some people have the problem of their device not showing up at all) but it does not receive any network signals, and i am literally right night next to my Router. In network tools if i view my device, wlan0 is says :

Hardware adress: 00:21:00:18:ab:3e
Multicast: Enabled
MTU: 1500
Link Speed: Not Available
State: Inactive

---

