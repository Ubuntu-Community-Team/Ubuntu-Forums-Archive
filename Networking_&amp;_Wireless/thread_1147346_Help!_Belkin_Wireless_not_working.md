---
title: "Help! Belkin Wireless not working"
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by kevinkms on 2009-05-03
I have just installed the latest release of Ubuntu but can't connect to the internet. I have a wirless G PCI card that works perfectly on windows.

I have installed ndiswrapper and installed the driver 'blkwgdv7' which is present. However, when I go to 'Configure Network' it says 'Could not find a network configuration tool'. ndiswrapper also gives me a start up error 'Unable to see if hardware is present.

I can't find 'Network' under system/administration so I cant even install my wireless that way. I cant install the network application under 'add/remove applications' because I have no internet access.

How can I get my wireless to work? Please Help. Thanks

---

### Post by hackerseraph on 2009-05-03
Hello, what is the exact model of your belkin card?

---

### Post by kevinkms on 2009-05-03
It is 802.11g F5D7000uk

---

### Post by hackerseraph on 2009-05-03
Looks like its a broadcom chipset. Broadcom cards require firmware along with the drivers to work. To install the firmware, you will need b43-fwcutter. Is there by any chance you could plug your machine into the lan. If so, and you can get internet access temporarily that way, you can go to System -> Administration -> Hardware drivers, and enable your wireless card that way.

---

### Post by kevinkms on 2009-05-03
I get this error when installing b43-fwcutter

kevin@kevin-desktop:~$ sudo apt-get install b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up b43-fwcutter (1:011-5) ...
--2009-05-03 19:17:15--  [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
Resolving downloads.openwrt.org... failed: Name or service not known.
wget: unable to resolve host address `downloads.openwrt.org'
dpkg: error processing b43-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 b43-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by hackerseraph on 2009-05-03
1. were you plugged into the internet?
2. try sudo apt-get update then try sudo apt-get intsall b43-fwcutter

---

