---
title: "BCM4311 on HP Pav DV6000 not working"
date: 2013-02-04
forum: Networking &amp; Wireless
---

### Post by torehund on 2013-02-04
Hello..

I'm a Ubuntu novice, and really struggelig with getting my wifi card to work. I have tried all sorts of recommondations on ubuntu help sites... tried fb43 , STA and bcma.. tried NDISWRAPPER and windows *.inf driver but WINE would not run the setup file..
Anybody with a working solution to this problem?

---

### Post by Bucky Ball on 2013-02-04
Welcome to the forums. Avoid ndiswrapper and uninstall as it will prevent any other fix from working.

Have you installed b43-fwcutter and firmware-b43-installer?

Try that and restart.

---

### Post by torehund on 2013-02-04
Thanks for your reply...

Uninstalled NDISWRAPPER, and reinstalled the 43's - restarted

Wifi indicator still orange (not working) and the "lshw -C network" reads

*-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d6000000-d6003fff

any ideas?

---

### Post by wildmanne39 on 2013-02-04
Hi, please do:
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
Thanks

---

