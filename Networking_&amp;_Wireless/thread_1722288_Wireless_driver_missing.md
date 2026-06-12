---
title: "Wireless driver missing"
date: 2011-04-05
forum: Networking &amp; Wireless
---

### Post by Linkmaster. on 2011-04-05
I just installed Ubuntu, and the wireless driver is not picking up the card, though its connected to many of the cards on the exact same type of computer. I'm not sure what to do, and I don't have access to an ethernet cable. Here's *lspci* output:
```
brian@Lenovo:~$ lspci 
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03) 
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03) 
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03) 
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02) 
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02) 
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02) 
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02) 
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02) 
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02) 
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02) 
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02) 
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) 
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02) 
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) 
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) 
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02) 
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02) 
05:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01) 
```

I see the card listed right there on the bottom, but I don't know how to get it working. I've tried *ifconfig* inputs, as well as *iwconfig* and *iwlist* inputs. Nothing is working that is within my knowledge.
If it helps, I have the driver for the wireless card that is designed for Windows, though its an .exe file, so I doubt it'll work

---

### Post by bkratz on 2011-04-05
There are instructions in this link on installing the driver either with or without internet access.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by Linkmaster. on 2011-04-05
And that did the trick! It was much easier to do then what other things I looked at. Thank you for the help, and I'll make sure to keep this handy. One question though: if I move the files to an x-HD, will I be able to do the same steps as listed the same? And will I be able to simply move only the 'pool' folder, or would I have to move the entire .iso, if its feasible. Thanks for your help again!

---

