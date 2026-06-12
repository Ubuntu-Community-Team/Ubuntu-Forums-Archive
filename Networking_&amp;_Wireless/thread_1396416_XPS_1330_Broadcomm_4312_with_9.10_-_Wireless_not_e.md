---
title: "XPS 1330 Broadcomm 4312 with 9.10 - Wireless not enabled"
date: 2010-02-02
forum: Networking &amp; Wireless
---

### Post by srajama on 2010-02-02
**1 ) Machine Brand and Model (PC/Laptop)**:
> Dell XPS 1330. 

**2 ) Wireless Brand, Model and Wireless Chipset:**

> 0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

Bus 002 Device 004: ID 05a9:7670 OmniVision Technologies, Inc. OV7670 Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 004: ID 0a5c:4503 Broadcom Corp.
Bus 003 Device 003: ID 0a5c:4502 Broadcom Corp.
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp.
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


**3 ) check interface:**$ iwconfig wlan0
> eth0      Link encap:Ethernet  HWaddr 00:15:c5:7f:15:e8
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe7f:15e8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9425 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8882 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8077725 (8.0 MB)  TX bytes:1513646 (1.5 MB)
          Interrupt:17

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:165 errors:0 dropped:0 overruns:0 frame:0
          TX packets:165 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6149 (6.1 KB)  TX bytes:6149 (6.1 KB)

lo        no wireless extensions.

eth0      no wireless extensions.

 
**4 ) Check for modules:**
> lsmod | grep wl 

Returns no results.

**6 ) Network configuration**
 >  *-network
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f1ffc000-f1ffffff
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:7f:15:e8
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=sb v3.04 ip=192.168.1.102 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:30 memory:f1bf0000-f1bfffff


**7 ) Scan for networks:**
> iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
****[B]

8) Ubuntu Version: [/B]
> lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 9.10
Release:        9.10
Codename:       karmic
****[B]
9 ) Kernel/architecture (including 32 vs. 64 bit): [/B]
> uname -mr
2.6.31-14-generic i686
**10 ) Restarting the network:**
> /etc/modprobe.d>sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                                                              Ignoring unknown interface eth0=eth0.
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
                                                                                                                                                                             [ OK ]


At this point, I have installed the STA driver for the device, though I have also tried with B43 (fwcutter). I have also tried with ndiswrapper with windows driver. All these cases, the end effect is the same. 

I can see "Wi-fi" LED light up. When I bring up the KDE control module for networks, "Wireless" is disabled. However, when I right-click on the network manager icon on the taskbar, I see "Enable Wireless" checked on. 

I am wondering if in the process of installing the ndiswrapprer drivers, I am messed up something?

---

### Post by pdc on 2010-02-02
I believe you needed the STA driver only

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

ndiswrapper (and b43) may be clashing; a three-way fight;

you may well need to blacklist ndiswrapper and b43: chili555 has made some posts recently which describe very well how to do this; 


..... I think you add blacklist ndiswrapper (and b43) to /etc/modules.blacklist.d but google to get the correct commands

---

### Post by srajama on 2010-02-02
Yes - It looks like a 3 way fight to the death - Unfortunately no one seems to be winning :-)

I believe I already have blacklisted b43. This is what my /etc/modprobe.d/blacklist says:

> /etc/modprobe.d> cat blacklist 
blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist ssb


This is my directory listing.

> /etc/modprobe.d>ls -al
total 56
drwxr-xr-x   2 root root  4096 2010-02-01 22:48 .
drwxr-xr-x 124 root root 12288 2010-02-01 22:35 ..
-rw-r--r--   1 root root  2497 2009-10-11 15:07 alsa-base.conf
-rw-r--r--   1 root root   198 2010-02-01 21:08 blacklist
-rw-r--r--   1 root root   325 2009-09-15 14:46 blacklist-ath_pci.conf
-rw-r--r--   1 root root   167 2010-02-01 22:10 blacklist-bcm43.conf
-rw-r--r--   1 root root  1603 2009-09-15 14:46 blacklist.conf
-rw-r--r--   1 root root   213 2009-09-15 14:46 blacklist-firewire.conf
-rw-r--r--   1 root root   662 2009-09-15 14:46 blacklist-framebuffer.conf
-rw-r--r--   1 root root   156 2009-10-11 15:07 blacklist-modem.conf
lrwxrwxrwx   1 root root    41 2010-01-13 04:23 blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r--   1 root root  1077 2009-09-15 14:46 blacklist-watchdog.conf
-rw-r--r--   1 root root  1751 2010-02-01 20:21 ndiswrapper


Am I missing something here?

---

### Post by pdc on 2010-02-03
if you do not intend to use ndiswrapper, I wonder if you would not be better adding it to the black list was well .........

---

### Post by srajama on 2010-02-03
Thanks for the responses. I added ndiswrapper to the blacklist and rebooted my machine. Still no luck. 
When I bring up the dialog for "Hardware drivers" for the STA driver, it says "This driver is activated but not currently in use".

 Does that mean something?

---

### Post by srajama on 2010-02-03
OK! Finally got it working  - I had the following line in my /etc/modules

> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
b43



Changed to 
> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
wl


Thanks a lot for your help!

---

