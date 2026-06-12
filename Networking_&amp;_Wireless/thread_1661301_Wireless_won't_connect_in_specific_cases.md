---
title: "Wireless won't connect in specific cases"
date: 2011-01-06
forum: Networking &amp; Wireless
---

### Post by 3602 on 2011-01-06
Most of the time my wireless works very well, connecting lightning-fast on boot with AC power. However here are two problems that I have noticed to-date:
1. Wireless will not connect if I boot on battery power. It won't connect even if I plug in the AC cable and do a reboot. Only solution is to reset the router (unplug power cable, wait, plug power cable).
2. Wireless will not connect after a Suspend, whether battery power or AC. Again, only solution is to reset the router.
Another computer, running Windows XP, do not have connection problems (yes, wireless). 
It is quite strange, maybe some power management settings are interfering with networking? I have* both laptop-mode-tools* and *pm-utils* (re-rolled) installed.
Thank you very much.

---

### Post by grahammechanical on 2011-01-06
I do not have a laptop. I understand that battery power will last longer if the wireless adapter is not active. In my opinion it makes sense for a machine not to power up the wireless adapter when booting on battery power. You may not want wireless networking. So, save battery power.

When you reboot the router it issues a wireless broadcast that is being picked up by the wireless adapter. This is why it seems to solve the problem. You should not need to reset the router to activate the wireless adapter in your laptop. What if you want to connect to a wireless network and you do not have access to the router?

Laptops usually have a keyboard key combination that activates the wireless adapter before booting the OS.

Also, by Right clicking the network icon, selecting the line Enable Networking, and clicking the tick mark will be removed and networking will be switched off. Clicking it again will enable networking. It will switch networking back on and the wireless adapter will scan for wireless networks. Doing the same to Enable Wireless will also work.

Regards.

---

### Post by 3602 on 2011-01-06
OK. Now. 
The wireless **isn't disabled** on battery power. The indicator spins and spins until "Disconnected". I click again and it spins again, repeat.
When it's disconnected (not spinning), I reset the modem,* then* it can connect.

---

