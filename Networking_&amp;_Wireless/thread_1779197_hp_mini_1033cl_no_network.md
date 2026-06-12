---
title: "hp mini 1033cl no network"
date: 2011-06-10
forum: Networking &amp; Wireless
---

### Post by xxzpxx on 2011-06-10
Hi, so was trying to switch to linux on my small netbook and decided to get acquainted using wubi first. I had some trouble instaling wubi but got it to work, however, now once i can boot into ubuntu i cannot connect to my network in any way; wireless or ethernet.... when i ping yahoo.com it says unknown host, and ifcpnfig gives eth0 and lo... im runing ubuntu 11.04... thanks for any help!

---

### Post by lesser on 2011-06-10
First of all, how do you normally connect? Run

```

lspci
lsusb

```
which will list your pci and usb devices. The will help us find the problem

---

### Post by xxzpxx on 2011-06-10
I usually connect via wireless on the netbook. This is what i get after I run those two commands:

netbook@ubuntu:~$ lspci 
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03) 
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03) 
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03) 
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02) 
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02) 
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02) 
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02) 
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02) 
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02) 
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02) 
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) 
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02) 
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) 
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02) 
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01) 


netbook@ubuntu:~$ lsusb 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 002: ID 10f1:1a08   
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by xxzpxx on 2011-06-10
any one?

---

### Post by xxzpxx on 2011-06-10
Really no one?? 

What does this line mean

01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01) 

How do I install the driver for BCM4312??

---

### Post by xxzpxx on 2011-06-11
SOLVED IT!!!!

Thanks all for reading...

all I had to do is follow this tutorial:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access)

:) finally....

---

