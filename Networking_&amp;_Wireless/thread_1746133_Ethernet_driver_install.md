---
title: "Ethernet driver install"
date: 2011-05-01
forum: Networking &amp; Wireless
---

### Post by davidself1001 on 2011-05-01
I am having problems with my eth0 interface stalling since i upgraded to 11.04.  It will be running fine and just stop.  If i disable it and re-enable it it works fine again for a while.  I'd like to try re-installing the driver.  How do i do that?  It is a Marvell 88E8056 PCI-E Gig Eth Controller.

---

### Post by davidself1001 on 2011-05-01
Ok, read how to install driver but during the process i can't get the shell file to run.  I get the error message below.  Any ideas on why this is happening?


root@david-desktop:/home/david/Desktop/DriverInstall# ./install.sh
./functions: 44: Syntax error: "(" unexpected

the DriverInstall dir has all the rite files, functions, install.sh, etc as specified in the readme.

Any help would be greatly appreciated.

---

### Post by davidself1001 on 2011-05-01
don't know if my eth0 is stable but i did manage to get the official marvell driver installed.  the problem with the ./install.sh command was that the shell tool is dash now so i had to run 'sudo bash ./install.sh' to get it to run the full bash script.

---

