---
title: "Can't get DLink N150 DWA-121 Adapter working on 11.10"
date: 2012-08-03
forum: Networking &amp; Wireless
---

### Post by skud78 on 2012-08-03
Been searching forums for a solution to getting my usb wireless device working on my machine.  Tried the following:

1.  Added to /etc/modprobe.d/blacklist 
      blacklist rtl8192cu
      blacklist rtl8192c_common

2.  Installed NDISwrapper 

3.  The ndiswrapper needs an .inf file to install a driver, as its meant  to use windows drivers on the linux system.  I tried installing the  linux driver file (from Dlink website) with ndiswrapper as suggested  above and it gives me an error asking for a .inf file.  As a flyer tried  renaming to .inf file and installing - comes up with error and lists as  invalid driver.

4.  installed .inf file with NDISwrapper - (downloaded .inf from Dlink  website), tried using the Win7x86, Win764, and WinXPx86 and Winx64.  

5. Win7 versions install successfully, but system doesn't pickup a wlan0  device on bootup.  WinXP versions cause major problems on the system  which doesnt boot up.   

Would be extremely grateful if someone can point out my mistake or find  another solution that works

---

### Post by skud78 on 2012-09-20
So problem solved by going out and buying the D-Link DWA 160 which works  out of the box with Ubuntu 11.10 - "plug and play".   Only catch is DWA  160 is more than twice the price of DWA 121 which works "plug and play"  on Windows 7.  

The not so cheap "free" O/S - hope the free software makes up for it

---

### Post by kurt18947 on 2012-09-20
Kind of late now but I wonder if the 8192cu driver from Realtek would have worked.  I have an Edimax nano USB wifi adapter that was recognized by Ubuntu but would not connect reliably.  The driver from Realtek was perfect.  And yes, I've learned to do a bit of research before purchasing hardware to be used on Linux systems.

---

