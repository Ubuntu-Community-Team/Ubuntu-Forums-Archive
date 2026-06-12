---
title: "Broadcom Corporation wireless card not detected after upgrade to 12.04"
date: 2012-04-30
forum: Networking &amp; Wireless
---

### Post by agatau on 2012-04-30
wireless stopped working after upgrade to 12.04

Dell Studio XPS 16, 64bit Kubuntu, Broadcom Corporation BCM4312

---

### Post by agatau on 2012-04-30
after carefully examining the output of the dmesg I realized that the firmware files for my particular card were not installed by the ubuntu installer. here is the command that solves this issue
```
sudo apt-get install firmware-b43-lpphy-installer
```
once you execute it, reboot the machine and everything will be fine
finally, I'm just wondering why the system installer, in spite of detecting the card, did not install the appropriate firmware

---

