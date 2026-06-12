---
title: "ubuntu 9.04 wireless atheros ar242x problem"
date: 2009-04-28
forum: Networking &amp; Wireless
---

### Post by aplaya1 on 2009-04-28
So I connected my computer up to wired connection to install the 'alternate atheros "madwifi" driver' from the Hardware Drivers screen. I activated this, but when i do iwconfig, no new connections are returned (after wired connection removed / reboot) It says that the ath5k driver has been installed, but in iwconfig, no new connections are returned:

computer information:::

uname -a
Linux ubuntu 2.6.28.11-server #42-Ubuntu SMP Fri Apr 17 02:48:10 UTC 2009 i686 GNU/Linux

cat /etc/issue
Ubuntu 9.04 \n \l

iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

pan0 no wireless extensions.

lspci | grep Atheros
Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

Thanks for helping me get my wireless working.

---

### Post by Bogdon6 on 2009-04-29
Did you reboot? I needed to reboot to get the midwifi driver to start working.

---

### Post by aplaya1 on 2009-04-29
Yes I did reboot.

---

### Post by TxRxBuffer on 2009-05-06
I'm experiencing the same thing. Helps us.

---

### Post by Aell on 2009-05-07
I'm also experiencing this problem after upgrading to 9.04

---

### Post by tmos22 on 2009-05-07
Hey guys try this guide it sorted mine out

[http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/](http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/)

---

