---
title: "Modems Auto Detect not working with Windows."
date: 2009-12-28
forum: Networking &amp; Wireless
---

### Post by Malizia on 2009-12-28
Why would my Ethernet card work just fine with Ubuntu, but not be auto detected for windows (XP Home edition)?  The lights on the modem port and my computer port light up when I'm running Ubuntu, but switch over to windows and neither light up. When i tried using verizon's install disc, it told me i have to two ethernet cards, and asks which one i would like to use. But the drop down menu doesn't have any options in it, and i can't go any farther then that without selecting one. And i see only one Ethernet port on my computer.

---

### Post by GeorgeVita on 2009-12-28
Hi **Malizia**, some ideas to try:

Open a terminal window and check output of: ```
sudo lshw | grep -i ethernet
``` this will show how many cards exist (ubuntu side).

Boot and press F2 (or F10 in some pcs) to check BIOS settings.

Check control panel at windows, remove any ethernet driver and install again. Better way is to follow instructions from motherboard manual (desktop) or from manufacturer site.

Regards,
George

---

