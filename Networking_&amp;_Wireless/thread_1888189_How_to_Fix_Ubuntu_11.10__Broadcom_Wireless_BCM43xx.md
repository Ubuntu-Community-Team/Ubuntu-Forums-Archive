---
title: "How to Fix Ubuntu 11.10  Broadcom Wireless BCM43xx connection"
date: 2011-11-28
forum: Networking &amp; Wireless
---

### Post by metcald on 2011-11-28
[FONT=Times New Roman][SIZE=3]This only seemed to work immediately following a clean install with no updates.  I did not have any joy getting this to work with an installation I had been playing around with (for hours) trying to get the wireless connection to work automatically after a reboot.  It may also be necessary afteran install when a reboot is required to run the “Boot repair disc” which can be downloaded from:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]
[/SIZE][/FONT]
  [FONT=Times New Roman][SIZE=3]http://sourceforge.net/p/boot-repair-cd/home/Home/[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]
[/SIZE][/FONT]
  [FONT=Times New Roman][SIZE=3]I needed to do this because I found that the new Ubuntu installation would not boot but just hung!  Just choose the standard repair options and it will boot no problems in future.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]
[/SIZE][/FONT]
  [FONT=Times New Roman][SIZE=3]As soon as Ubuntu loads do not do any updates but openaterminalwindowandtypethefollowingcode:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]
[/SIZE][/FONT]
  [FONT=Times New Roman][SIZE=3]Line 1.  sudoapt-getupdate[/SIZE][/FONT]
  [FONT=Times New Roman][SIZE=3]Line 2.  sudoapt-getinstallfirmware-b43-installer[/SIZE][/FONT]
  [FONT=Times New Roman][SIZE=3]Line 3.  sudoapt-getremovebcmwl-kernel-source[/SIZE][/FONT]
  
  [FONT=Times New Roman][SIZE=3][FONT=&quot]Only the first 2 lines should be necessary and running line 3 returned “[/FONT]bcmwl kernel source code was not installed” on my Acer Extensa 5210[/SIZE][/FONT]
  
  [FONT=Times New Roman][SIZE=3][FONT=&quot]At this point the wireless applet in the task bar will still show the wireless as not available and greyed out will be “missing firmware”.  So the next step is to install the firmware.[/FONT][/SIZE][/FONT]
  
  [FONT=Times New Roman][SIZE=3][FONT=&quot]Open the “Ubuntu Software Centre” and after loading search for “b43” which should give you 4 options. Select and install “Installer package for the firmware for the b43 driver”.  After it installs your wireless network connection should now automatically open (assuming that you have already created a new wireless connection with the name and password - and correctly configured).[/FONT][/SIZE][/FONT]
  
[FONT=Times New Roman][SIZE=3]  [FONT=&quot]Reboot your computer and check that the wireless connection is automatically initiated.  It worked for me anyway so good luck!

Dave
[/FONT][/SIZE][/FONT]

---

