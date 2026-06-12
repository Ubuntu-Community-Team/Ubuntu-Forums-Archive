---
title: "Ubuntu Internet: No Cable or Wireless Internet Working"
date: 2009-03-08
forum: Networking &amp; Wireless
---

### Post by seeker111388 on 2009-03-08
I recently bought a netbook, and MSI U120, and I partitioned the computer with Ubuntu 8.1.  At first, wireless would not work, only ethernet cable.  I updated the kernal, rebooted, and found that then the cable internet does not work.  I've tried troubleshooting and all I get are errors. It seems that the OS doesn't read the internet capability of my netbook.
I am a complete noob at Ubuntu and Linux in general but I really want to learn. 
Please help me fix this problem, and let me know what other info you need from it. 

A little random but here are some terminal entries if it helps in anyway:



sudo dpkg -i linux-rtl8187se-*.deb
dpkg: error processing linux-rtl8187se-*.deb (--install):
cannot access archive: No such file or directory
Errors were encountered while processing:
linux-rtl8187se-*.deb

sudo lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)

~/Desktop$ sudo dpkg -i linux-rtl8187se-*.deb 
Selecting previously deselected package linux-rtl8187se-modules.
(Reading database ... 99834 files and directories currently installed.)
Unpacking linux-rtl8187se-modules (from [email]linux-rtl8187se-modules-1023.3@2.6.27.13.16.deb[/email]) ...
dpkg: dependency problems prevent configuration of linux-rtl8187se-modules:
linux-rtl8187se-modules depends on linux-generic (>= 2.6.27.13.16); however:
  Version of linux-generic on system is 2.6.27.7.11.
dpkg: error processing linux-rtl8187se-modules (--install):
dependency problems - leaving unconfigured
Errors were encountered while processing:
linux-rtl8187se-modules

---

### Post by ugm6hr on 2009-03-08
I don't have that netbook, but have some thoughts / details:

1. The new Intrepid kernel does not work with your ethernet: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/322916](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/322916)
I would recommend just sticking to the older -7 kernel for now.

2. It appears you have already tried some compiled driver, which won't install.  This suggests there is a working version:
[http://forums.msiwind.net/debian/rtl8187se-drivers-for-ubuntu-and-deb-packages-t4954.html](http://forums.msiwind.net/debian/rtl8187se-drivers-for-ubuntu-and-deb-packages-t4954.html)

3. The original wifi bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246141](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246141)

---

