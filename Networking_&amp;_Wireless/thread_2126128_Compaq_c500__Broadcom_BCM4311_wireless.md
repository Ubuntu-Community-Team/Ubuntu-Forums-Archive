---
title: "Compaq c500 / Broadcom BCM4311 wireless"
date: 2013-03-16
forum: Networking &amp; Wireless
---

### Post by Arrowman2 on 2013-03-16
Hello,

I'am new to Ubuntu, and I have been trying to get my wifi card running with Ubuntu 12.04. When I type the command lshw -C network, I can see that the card has no logical name, so I guess the driver is not installed properly. Could anyone help me further? I tried installing the Broadcom linux driver from the Broadcom website, but it seems that the code in this installation is not working for the latest versions of Ubuntu.

  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=wl latency=0
       resources: irq:18 memory:80000000-80003fff

Thanks,

---

### Post by varunendra on 2013-03-16
Welcome to the forums Arrowman2 ! :)

If you have a wired connection available, connect to it and do -
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
sudo apt-get install b43-fwcutter firmware-b43-installer
```
Enter the above commands in a terminal (Ctrl+Alt+T), then disconnect the wired connection and try to connect via wireless. Do a restart if required.

Post back the result. Thanks!

---

### Post by Arrowman2 on 2013-03-16
Thanks very much, after a restrart the wifi works perfectly now

---

