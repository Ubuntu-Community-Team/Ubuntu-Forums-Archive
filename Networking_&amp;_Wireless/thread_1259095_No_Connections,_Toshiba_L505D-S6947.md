---
title: "No Connections, Toshiba L505D-S6947"
date: 2009-09-05
forum: Networking &amp; Wireless
---

### Post by leversandgears on 2009-09-05
Hello All,

I've just purchased an L505D-S6947 laptop made by Toshiba.  Neither ethernet or wireless appear to be working.  The network manager applet does not recognize that there is a wireless card present, either (to mean that clicking on the icon does not have the disable wireless radio check box present.)

So far, I have verified that ndisgtk is present and have a driver for the ethernet card installed without error, however it does not work.  Furthermore, when I used ndisgtk to install the wireless driver from Toshiba, I get an error of "Unable to determine if hardware is present."

I thought that it may be an issue with ACPI, so I disabled it in /boot/grub/menu.lst, however that had no effect on the problem.

I have the most current Windows drivers from Toshiba for the card, but nothing seems to be going quite right.  I am using the x64 version of 9.04, and downloaded the install today.

---

### Post by ugm6hr on 2009-09-06
It is best to start afresh when asking for wifi help, since the various edits and ndiswrapper changes will affect our advice.

Try a LiveCD again with wired and wireless, and give details as in my Wifi help link below.

---

