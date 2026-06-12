---
title: "wireless was working, but after fresh install"
date: 2008-12-29
forum: Networking &amp; Wireless
---

### Post by Brian_Newbie on 2008-12-29
I freshly installed Ubuntu 8.10 intrepid but now my wireless is not working. My system is x86-64 and ndiswrapper worked fine to detect the available wireless networks but I cannot find the thread that got my wireless working. 

I know that I had to "blacklist" HAL somehow when installing ndiswrapper and that there were separate instructions for 32 bit and 64 bit systems in that thread. The thread ended with rebooting the computer. 

Does anyone know the location of this thread? Or alternate ways to disable HAL and install ndiswrapper?

card info: atheros AR5007EG, AR242X, Acer laptop

---

### Post by 67GTA on 2008-12-29
It should work without ndiswrapper. Go to Menu>System>Administration>Hardware Drivers. Deactivate the atheros module in use and reboot. After rebooting, put in your 8.10 install CD and add it as a repo. Then install ```
linux-backports-modules-intrepid-generic
``` from the CD. You should have wireless working after rebooting.

---

