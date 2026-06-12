---
title: "WUSB54G v1"
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by untappedpilot2 on 2008-12-20
So today I picked up a WUSB54G and I'm really looking forward to getting it working because I've been playing around with the aircrack-ng suite for some time now. As it turns out this device is supported and I *thought* I wouldn't have to do too much fiddling around with it to get it working. Unfortunately as usual this is not the case. Anyway the WUSB54G v1 uses the prism chipset and the prism54 driver correlates with it. I'm really having some trouble getting this installed and everywhere I've looked online ndiswrapper seems to be the preferred (if not only) method of getting it working. However, for me to make use of aircrack-ng this is not an option. I would really appreciate some help getting this setup. I think the prism54 driver is native to Ubuntu (I'm running Xubuntu 8.10) however it doesn't seem to pick it up. The only command that confirms it should be seeing it is:

```
#lsusb
Bus 002 Device 002: ID 058f:6391 Alcor Micro Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 1915:2234 Linksys WUSB54G 802.11g Adapter
Bus 001 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

lshw -C network, iwconfig, ifconfig, all yeild 0 results.

---

