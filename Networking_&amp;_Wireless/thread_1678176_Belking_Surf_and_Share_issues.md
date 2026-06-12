---
title: "Belking Surf and Share issues"
date: 2011-01-29
forum: Networking &amp; Wireless
---

### Post by Rogueninja1 on 2011-01-29
Hello all,

I have recently installed Ubuntu 10.10 on my system, which I believe to be very useful, but one problem is that I cannot get it to recognize that I have a wireless usb device.  The disk comes with only windows drivers, and ubuntu does not appear to have any sort of default wireless usb driver for my device.  I have looked up the problem, and apparently there is a solution, but it is not clear to me what I should do.  The following things I have tried (to no avail):

[LIST]
[*]Used ndiswrapper to install WinXP, Win2K, and WinVista variants of the driver.  Says "Driver installed" and "Hardware Present", but when I type iwconfig or ifconfig, no wireless device is listed.
[*]Installed the "Linux" driver from Realtek, ran make and make install, but received hundreds of errors during installation.  No wireless device appears anywhere
[/LIST]
I do not know if I have done it all cleanly or not, as it appears that I have tried some of the methods more than once, so if there is any way to make sure I get a fresh start, please let me know (other than os reinstall).  Hopefully one of you has some suggestions for this issue.

UPDATE:  It seems that I was trying to use the 32 bit drivers for my 64 bit kernel, but when I tried the 64 bit drivers my ndiswrapper froze, and seems broken.  I cannot use the ndiswrapper -l command, it just hangs.  The GUI is also just a blank white window.  Is there any way to fix this?
Thanks!
[LEFT]
[/LEFT]

---

