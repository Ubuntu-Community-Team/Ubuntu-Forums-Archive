---
title: "Simple fix for  Broadcom STA wireless driver without network 9.10"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by the_maplebar on 2009-11-05
Here is a simple way I got my Dell D820 with Broadcom BCM4312.  It should work with any of the broadcom chips that use the STA driver.  

Prerequisite:  I was able to boot using the 9.10 live CD and get networking working.  The live CD recognized the hardware and installed the proprietary drivers, but after installation my computer did not.

Steps to get the Broadcom wireless driver working:
1)  After installing 9.10 and booting up, insert the 9.10 live cd
2)  Ubuntu should prompt you that the CD has APT sources, Select "yes" or "ok" to use the CD APT repository.
3)  Open Synaptic Package Manager.
3a) If you didn't get the prompt to add the CD APT sources before, just go to Edit -> Add CDRom now.
4) Look for bcmwl-kernel-source, install, reboot and you should be good.

Note, the Broadcom STA driver states that it works with the following hardware: Broadcom's BCM4311-, BCM4312-, BCM4321-, and
BCM4322-based hardware

---

