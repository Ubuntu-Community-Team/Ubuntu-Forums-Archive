---
title: "Nvidia Optimus GeForceGT740m"
date: 2013-09-18
forum: Multimedia Software
---

### Post by SchrodingerCat on 2013-09-18
Hi,
i have probem installing Drivers. I followed the following guide:
[http://followthegeeks.com/a-noobs-guide-to-installing-nvidia-optimus-driver-in-ubuntu/](http://followthegeeks.com/a-noobs-guide-to-installing-nvidia-optimus-driver-in-ubuntu/)

so i just installed bumblebee and bumblebee-nvidia.. but my system seems not to detect the Nvidia card.
Any help?

---

### Post by Yellow Pasque on 2013-09-18
You need nvidia driver 319.32 or later to support the 740m
Bumblebee's also changed a bit: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
```
sudo apt-get install bumblebee virtualgl linux-headers-generic mesa-utils
```
Reboot and check:
```
optirun glxinfo
optirun glxspheres
```
Success?

---

