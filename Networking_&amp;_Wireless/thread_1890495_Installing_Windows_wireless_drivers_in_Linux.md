---
title: "Installing Windows wireless drivers in Linux"
date: 2011-12-03
forum: Networking &amp; Wireless
---

### Post by travlemon on 2011-12-03
Hello,

I'm sure it's an outdated type of tutorial to make, for ndiswrapper and the "Windows Network Drivers" utility, but I've been wanting to make one for a while, and noticed a significant difference in the workflow on Ubuntu 11.10 based systems. 

This tutorial shows 2 methods on installing a Windows wireless driver in Linux/Ubuntu.  The first method shows how to do it on Mint 12, using the "Windows Network Drivers" utility, the GUI for ndiswrapper.

The second method shows how to do it from the command line with ndiswrapper.  I also gave a couple of tips on how to obtain ndiswrapper, if it's not installed on your system by default.

The difference between the old workflow and new is that ndiswrapper writes its configuration to a different file in 11.10.  Previously, it was written to **/etc/modprobe.d/ndiswrapper.conf**, but in 11.10 it writes it to **/etc/modules.conf**.  This prevents the system from initializing the wireless card at boot.  I simply explain how to symlink **modules.conf** to the **/etc/modprobe.d** folder and rename it to **ndiswrapper.conf**.  The system will then see the ndiswrapper.conf file that it wants, and follow it to modules.conf, and initialize the card at boot.


Anyway, here's the link to the tutorial video:
[http://www.youtube.com/watch?v=wchimaoe9KE](http://www.youtube.com/watch?v=wchimaoe9KE)

Hope it's helpful!

---

