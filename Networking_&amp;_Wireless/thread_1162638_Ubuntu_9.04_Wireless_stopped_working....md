---
title: "Ubuntu 9.04 Wireless stopped working..."
date: 2009-05-17
forum: Networking &amp; Wireless
---

### Post by Linuxperiment on 2009-05-17
Hi everyone, I did a successful Ubuntu 9.04 install on my Dell Mini 9 today, and the wireless worked great and everything, until I did a reboot. The internet just STOPPED working, and I even downloaded all of the updates with use of an ethernet cable, not still no wireless. I even went as far as to stop using Ubuntu 9.04 and use Ubuntu 8.10 and the SAME exact thing happened. No wireless after a reboot.

Any ideas guys? Both Ubuntus were installed with use of a Sandisk USB Flash Drive and I believe my wireless card is the Broadcom one that comes with the Mini 9.

I'm still a Linux newbie trying to get the hang of things, so don't assume I know how to fix any of this stuff that well :(

---

### Post by DakabinSHS on 2009-05-17
Use the terminal to connect to the wireless
connect <connectionname>
you may need to install a package

---

### Post by superprash2003 on 2009-05-18
post output of the following from the terminal
1)lshw -C network
2)iwconfig
3)sudo iwlist scanning

---

