---
title: "Make Scanner of my network printer to work"
date: 2012-02-11
forum: Networking &amp; Wireless
---

### Post by Liova99 on 2012-02-11
Hello
I use my Notebook on my work, i have Ubuntu 11.10. i Conect to the ofice network with Ethernet, everithing was fine, the printer (HP laserjet m1120) working nice, but yesterday i was neded to scan a documet but i can't do it. I try "xsane" "Skinlite" "HPLIP" but i cannot locate my Scanner. I didn't find anithing to help my in Google :) Please help you are my only hope.... ](*,)

P.S. Sory for my bad Englesh :oops:

Maby it will help: The printer is conected via usb to a windows pc!

---

### Post by elv5034 on 2012-02-12
You probably have to install the driver for the scanner. The same thing happened with me, but I have a Canon printer/scanner and it was easier to find support for that. Here are a few web pages that might help: 

[http://hplipopensource.com/hplip-web/index.html?](http://hplipopensource.com/hplip-web/index.html?)
[http://linuxers.org/howto/how-setup-and-configure-hp-printer-or-scanner-ubuntu-or-fedora-linux](http://linuxers.org/howto/how-setup-and-configure-hp-printer-or-scanner-ubuntu-or-fedora-linux)
[http://www.adminlive.net/adminlive/open-source-support/install-hp-scanjet-g2410-scanner-on-ubuntu](http://www.adminlive.net/adminlive/open-source-support/install-hp-scanjet-g2410-scanner-on-ubuntu)

I'm a newbie, so I'm sorry I can't help any more than that.

---

### Post by Liova99 on 2012-03-02
Thank's for the answer, but nothing can't help the situation :-| ....

---

### Post by Bucky Ball on 2012-03-02
Follow the steps here:

[http://hplipopensource.com/node/334](http://hplipopensource.com/node/334)

If you can already print and the printer is connected to the network you can skip the part about configuring IP address, etc. As far as HP are concerned scanning on this machine is fully supported.

Your problem could be that you are actually networking to another machine to get to the printer and the printer is not connected to a router (LAN network). In this case the steps in the link above maybe irrelevant. This printer should be plugged into the work router via an ethernet cable (or wirelessly if it has that capability) for optimum results and accessibility for everyone. Good luck.

---

