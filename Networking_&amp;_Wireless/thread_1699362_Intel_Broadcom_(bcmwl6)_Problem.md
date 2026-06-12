---
title: "Intel Broadcom (bcmwl6) Problem"
date: 2011-03-03
forum: Networking &amp; Wireless
---

### Post by Epiplon on 2011-03-03
First of all, I have a HP Pavilion dv6-2155dx Entertainment Notebook with Broadcom Wireless Lan Driver.

I didn't want to bother anyone with this, but I just could't find a solution.
I was happy using Ubuntu 10.04 LTS Desktop Edition, because the wifi was working fine, but I messed everything up dealing with networking in terminal.
So formated and now I have Ubuntu 10.10 Netbook Edition, but that didn't solved my problem at all, because my wifi driver still unfunctional.
Before anything, I tried commands like "dbus restart" and "network restart".
So after reading that I can install by getting ndisgtk and the *.inf* file, I downloaded the right driver from HP Support's page of my notebook. Extracted the package with Wine (got some error because I wasn't running Win7, of course, but that doesn't matter.).

I did this:
[http://img638.imageshack.us/i/screenshotdxl.png/](http://img638.imageshack.us/i/screenshotdxl.png/)

And this is my final result:
[http://img28.imageshack.us/i/drivers.png/](http://img28.imageshack.us/i/drivers.png/)

Technical informations:

> 
1) HP Pavilion dv6-2155dx Entertainment Notebook
2) Intel Corporation Centrino Broadcom Wireless-N 1000
(don't know the informations for sure, tried every hint)
3)
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

4)
 *-network DISABLED      
       description: Wireless interface
       product: Centrino Wireless-N 1000
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:1e:64:8c:74:9a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.35-22-generic firmware=128.50.3.1 build 13488 latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:45 memory:d5400000-d5401fff


Kernel: 2.6.35-22-generic i686


---

### Post by Epiplon on 2011-03-03
I already solved the problem. Don't know how, but I solved.

---

