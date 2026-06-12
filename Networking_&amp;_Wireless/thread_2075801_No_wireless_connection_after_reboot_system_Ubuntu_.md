---
title: "No wireless connection after reboot system Ubuntu 12.10"
date: 2012-10-24
forum: Networking &amp; Wireless
---

### Post by moroccan92 on 2012-10-24
When i try this lines in terminal , my computer find finally my wireless connection 
but when i reboot system , it doesn't work
what's happening ????

sudo modprobe -r b43 ssb wl sudo apt-get remove bcmwl-kernel-source  sudo apt-get install build-essential dkms linux-headers-generic sudo apt-get install bcmwl-kernel-source
my card is broadcom 4312

---

