---
title: "lenovo G560 WLAN driver"
date: 2010-04-08
forum: Networking &amp; Wireless
---

### Post by shara on 2010-04-08
hi
I change my laptop from HP to lenovo G560 series .
but I have a problem with wireless device in LENOVO .
I can't find any driver to Lenovo G560 , can any body help me to find it?

for more information about lenvo see this link :

[http://shop.lenovo.com/SEUILibrary/controller/e/web/LenovoPortal/en_US/catalog.workflow:category.details?current-catalog-id=12F0696583E04D86B9B79B0FEC01C087&current-category-id=533B028107C74639B0C8F655F9269710](http://shop.lenovo.com/SEUILibrary/controller/e/web/LenovoPortal/en_US/catalog.workflow:category.details?current-catalog-id=12F0696583E04D86B9B79B0FEC01C087&current-category-id=533B028107C74639B0C8F655F9269710)

thanks

---

### Post by chili555 on 2010-04-08
The link you gave us doesn't tell us much about the wireless card. Please open Applications > Accessories > Terminal and do:```
lspci -nn
```Please post the part relating to your wireless card, or, if in doubt, post it all. We will then have a better idea how to proceed.

---

### Post by shara on 2010-04-08
> 
00:00.0 Host bridge [0600]: Intel Corporation Arrandale DRAM Controller [8086:0044] (rev 12)
00:01.0 PCI bridge [0604]: Intel Corporation Arrandale PCI Express x16 Root Port [8086:0045] (rev 12)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 05)
00:1c.2 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 [8086:3b46] (rev 05)
00:1c.4 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 [8086:3b4a] (rev 05)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
01:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:0a75] (rev a2)
01:00.1 Audio device [0403]: nVidia Corporation Device [10de:0be3] (rev a1)
06:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4727] (rev 01)
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
ff:00.0 Host bridge [0600]: Intel Corporation QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
ff:00.1 Host bridge [0600]: Intel Corporation QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
ff:02.0 Host bridge [0600]: Intel Corporation QPI Link 0 [8086:2d10] (rev 02)
ff:02.1 Host bridge [0600]: Intel Corporation QPI Physical 0 [8086:2d11] (rev 02)
ff:02.2 Host bridge [0600]: Intel Corporation Device [8086:2d12] (rev 02)
ff:02.3 Host bridge [0600]: Intel Corporation Device [8086:2d13] (rev 02)



can this details help you?
thank you sir

---

### Post by chili555 on 2010-04-08
Do you have internet connectivity with your wired ethernet? If so, please open a terminal and do:```
sudo apt-get install bcmwl-kernel source
```After it's installed, detach the ethernet cable, reboot and your wireless should be working.

---

### Post by shara on 2010-04-09
thanks chili
but don't work it.
I install bcmwl-kernel but I can't access to wireless :(
I can't find any driver for Broadcom wireless driver :(
please help me

---

### Post by chili555 on 2010-04-09
Please do:```
sudo modprobe wl
iwconfig
dmesg | grep -e wl -e 06:00
```Thanks!

---

### Post by shara on 2010-04-09
> 
root@sharacle:~# modprobe wl
root@sharacle:~# iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

ppp0      no wireless extensions.

root@sharacle:~# dmesg | grep -e wl -e 06:00
[    0.705868] pci 0000:06:00.0: reg 10 64bit mmio: [0xd9100000-0xd9103fff]
[    0.706027] pci 0000:06:00.0: supports D1 D2
[    0.706028] pci 0000:06:00.0: PME# supported from D0 D3hot D3cold
[    0.706036] pci 0000:06:00.0: PME# disabled



dear chilli
I do your codes
:(
I can not see any changes
there is not any driver for solving this problem :(

---

### Post by oleink on 2010-04-09
There are drivers but you may have to use ndiswrapper.  I dont know if there is a native driver for your system.  I finally found something about the card but not enough detail

---

### Post by chili555 on 2010-04-09
Please try this:```
sudo apt-get remove -- purge bcmwl-kernel-source
sudo apt-get remove linux-backports-modules-*
sudo apt-get install bcmwl-kernel-source
```[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/484643](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/484643)

See post #5.

---

### Post by oleink on 2010-04-09
Actually that may work just as well considering software preferences and software drivers

---

### Post by Messerjocke on 2010-04-21
The WLAN chip is a BCM 4313 and there is a working driver for it.

Check this page:

[http://www.linlap.com/wiki/lenovo+g560](http://www.linlap.com/wiki/lenovo+g560)

Cheers,
Messerjocke

---

### Post by shara on 2010-04-23
thank you sir
I installed that and wireless Driver is installed and work fine. just when I'm rebooting the system Wlan is turned off :(
what can I do to run this drivers as starting the linux?

---

