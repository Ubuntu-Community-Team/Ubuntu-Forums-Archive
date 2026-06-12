---
title: "Ubuntu 9.04 &amp; gnome-network-admin dialup configuration."
date: 2009-08-02
forum: Networking &amp; Wireless
---

### Post by duanekf2jc on 2009-08-02
I'm attempting to setup Ubuntu 9.04 to get online with a US Robotics PCI dialup modem. Using another PC, I downloaded the "gnome-network-admin" program. When I setup the modem as ttyS0, then save the settings, the screen reverts to "point to point ethernet interface". I removed, then reinstalled gnome-network-admin program, but that didn't help.I can use the PPP dialer to get online, but Firefox doesn't work. I tried to download, transfer, install gnome-PPP & wvdial, but ran into dependency problems. I never thought I would be using VISTA to download, & transfer files to Ubuntu. Thanks for your help!

---

### Post by GeorgeVita on 2009-08-02
Hi **duanekf2jc**,
sometimes when you connect via a 'terminal' method **firefox** starts in '**offline mode**' which can be turned online again by pressing **ALT-F W** into firefox.

If you need **wvdial+dependencies** without internet connection to the Ubuntu running PC read:
[http://ubuntuforums.org/showthread.php?p=7245790#post7245790](http://ubuntuforums.org/showthread.php?p=7245790#post7245790)

Regards,
George

---

### Post by duanekf2jc on 2009-08-05
Hi George,
   Thanks for your help. I downloaded gnome-ppp, wvdial, and the dependencies for wvdial using my Vista PC, then transferred the files via a thumb drive to Jaunty. When I setup gnome-ppp, I had to create ATZ4 for the first initialization string. I am able to get online, but when I open firefox, it comes up offline & has to be manually changed to go online.

---

### Post by gmrple on 2009-08-06
Thanks George!!! I've been playing around with an EVDO card for a while... due to some usbserial issues and bad spelling, I had been unable to get it to connect to the network until last night, but I couldn't access the internet because firefox was in offline mode :) Now everything is working properly.

---

