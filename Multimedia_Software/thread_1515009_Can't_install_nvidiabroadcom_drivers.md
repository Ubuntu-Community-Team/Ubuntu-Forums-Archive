---
title: "Can't install nvidia/broadcom drivers"
date: 2010-06-21
forum: Multimedia Software
---

### Post by samgrylls on 2010-06-21
Hi, I just installed ubuntu 10,04, and I'm having trouble getting proprietary drivers installed.  When I go to system > drivers and try to install them this way, I get the following error message: InstallArchives failed.  I tried the following command:
sudo apt-get update
I then checked the driver status:
sudo jockey-text -l
then I did the following:
sudo jockey-text -e xorg:nvidia_current
and it says:
xorg:nvidia_current - NVIDIA accelerated graphics driver (Proprietary, Enabled, Not in use)
Now when I try to open the game that I needed to install the driver for in the first place, the screen simply flashes once and nothing happens.  I'm not sure what's wrong, any help would be greatly appreciated!

---

