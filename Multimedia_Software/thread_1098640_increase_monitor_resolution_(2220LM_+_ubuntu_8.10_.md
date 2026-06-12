---
title: "increase monitor resolution (2220LM + ubuntu 8.10 64 bit)"
date: 2009-03-17
forum: Multimedia Software
---

### Post by mastupristi on 2009-03-17
I have new pc, acer aspire M5641 with **ATI HD4650**, monitor Samsung **SyncMaster 2220LM**. I just installed ubuntu 8.10 64 bit.
Unfortunately monitor resolution is set to 1280x1024, and there is no higher resolution. The monitor support 1680x1050. Do I need to install the restricted driver or how can I configure the monitor?

thanks

---

### Post by vnvnvn2000 on 2009-03-17
Go to System->Administration->Hardware Drivers. If it shows that there are available drivers, check the checkbox and it will download and install the driver.

If you have nvidia or ati there is a tool called envyng. It downloads the latest drivers and installs them. To install envyng open a terminal and type:
sudo apt-get install envyng-gtk

Than run envy from the menu Applications->System Tools, i think.

---

