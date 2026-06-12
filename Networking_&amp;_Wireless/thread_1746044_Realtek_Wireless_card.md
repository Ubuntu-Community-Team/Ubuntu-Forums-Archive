---
title: "Realtek Wireless card"
date: 2011-05-01
forum: Networking &amp; Wireless
---

### Post by yungballla6 on 2011-05-01
Was just wondering if there is anyone else besides me having trouble with there **realtek wireless cards** in ubuntu. My wifi becomes unstable and eventual I cannnot download/surf the web.
***PLEASE HELP***. i really love ubuntu but i need internet stability.

---

### Post by northd_tech on 2011-05-01
I've had a LOT of trouble with a Realtek 8192E under 64-bit Ubuntu.  Can you post the results of the following terminal commands?

```
lspci | grep work
sudo lshw -C network
```

---

### Post by yungballla6 on 2011-05-01
> **northd_tech said:**
> I've had a LOT of trouble with a Realtek 8192E under 64-bit Ubuntu.  Can you post the results of the following terminal commands?

```
lspci | grep work
sudo lshw -C network
```
I will post the results of when my internet works and when it doesnt because my problem is my connections ends up dropping after 5 minutes or so and i cannot reconnect.

**At 7:38 pm**
louie@louie-HP-G62-Notebook-PC:~$ lspci | grep work
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller (rev 10)
louie@louie-HP-G62-Notebook-PC:~$ sudo lshw -c network
[sudo] password for louie: 
  *-network               
       description: Wireless interface
       product: RTL8191SEvA Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 10
       serial: 70:f1:a1:e8:b1:1a
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0017.0507.2010 firmware=63 ip=192.168.0.153 latency=0 link=yes multicast=yes wireless=802.11bg
       resources: irq:16 ioport:3000(size=256) memory:d3500000-d3503fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: c8:0a:a9:f0:bf:c7
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:d1410000-d1410fff memory:d1400000-d140ffff memory:d1420000-d142ffff
louie@louie-HP-G62-Notebook-PC:~$ 

At 7:58 (when internet stopped working)
louie@louie-HP-G62-Notebook-PC:~$ lspci | grep work
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller (rev 10)
louie@louie-HP-G62-Notebook-PC:~$ sudo lshw -C network
[sudo] password for louie: 
  *-network               
       description: Wireless interface
       product: RTL8191SEvA Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 10
       serial: 70:f1:a1:e8:b1:1a
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0017.0507.2010 firmware=63 ip=192.168.0.153 latency=0 link=yes multicast=yes wireless=802.11bg
       resources: irq:16 ioport:3000(size=256) memory:d3500000-d3503fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: c8:0a:a9:f0:bf:c7
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:d1410000-d1410fff memory:d1400000-d140ffff memory:d1420000-d142ffff
louie@louie-HP-G62-Notebook-PC:~$

---

### Post by yungballla6 on 2011-05-01
also this problem was occurring on 64 bit version. I switched to 32 bit to see if the problem would be solved.....it didnt.

---

### Post by yungballla6 on 2011-05-01
Bumppppp please

---

### Post by yungballla6 on 2011-05-01
bump

---

### Post by garvinrick4 on 2011-05-01
It will most likely be a driver issue. You have to google your wifi card and or driver and Ubuntu in same line and see if there has been issues and if there was a fix put out.
 I have a hp also with intel wifi card and had to put in line of code to disable n feature
for same reason as you. Found fix by researching, check launchpad also. This will give
your thread a bump. If it is a standard card for HP then there is a lot of users who have had this problem. Good luck. when you find it there will be directions on how to fix. Launchpad.net always has good directions, look in upper right of Ubuntu forums page.

---

### Post by northd_tech on 2011-05-01
> **yungballla6 said:**
> 
02:00.0 Network controller: **Realtek** Semiconductor Co., Ltd. **RTL8191SEvA Wireless** LAN Controller (rev 10)

  *-network               
       description: Wireless interface
       product: **RTL8191SEvA Wireless** LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 10
       serial: 70:f1:a1:e8:b1:1a
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes **driver=rtl819xSE** **driverversion=0017.0507.2010** **firmware=63** i

I've boldfaced the most relevant parts of that above- it's a Realtek **8191SEvA** (which I'd read as an 8191SE [COLOR=Red]**v**[/COLOR]ersion [COLOR=Red]**A**[/COLOR], but I'm not certain on that bit).

In my search here, that came up on the following thread, and pages 7 & 8 seemed the most hopeful/helpful- see the posts by "VideoRoy":

[B]Wireless stops working periodically Ubuntu 10.10 
[http://ubuntuforums.org/showthread.php?t=1597881](http://ubuntuforums.org/showthread.php?t=1597881)

I'll need to do some more searching through my notes, but I had to email "Kidman" at Realtek support and blacklist some modules before I was finally able to get that Realtek 819**2E **working under 64-bit Ubuntu (after many months and several Realtek driver versions).  Most people (including my relative whose 64-bit Toshiba I was working on) had little to no trouble with 32-bit Realtek.

As garvinrick4 said, this is probably a "new" old problem due to some kernel tweaking in the 11.xx versions.  Once you/we get it figured out, I'd keep some good notes and your source tarballs or .deb files handy (as well as keeping 2-3 "old" Linux kernels with WORKING wireless for future reference in your bootloader).

Also, the Realtek 819**2SE** is very different from the Realtek 819**2E** (from my experience), but I believe that your 819**1SEvA** should **probably** use the same driver as the Realtek 819**2SE**.

---

