---
title: "Inspiron B150 wifi issue"
date: 2011-10-25
forum: Networking &amp; Wireless
---

### Post by 2Mobile on 2011-10-25
Hello everyone.
I've recently downloaded Ubuntu 10.4 on an older laptop I have to learn how to use linux. I'm pretty much teaching myself which is no small matter since I'm old. I've hit a wall, though, and I've looked for an online solution for it for days with no luck. So, if anyone has any free time or advice to where I can find the answer, I would appreciate it.

My issue is wifi connection, which I've learned is common. I've followed directions but when I get to a driver search, it comes up with no proprietary driver. Nothing on the list at all. Any suggestions?

here is some info i've seen posted in other threads:

00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller [8086:2668] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 [8086:2666] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03)
02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
02:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

and:

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

and:

  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:95:fe:2e
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=10.0.1.4 latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:18 memory:dfbfc000-dfbfdfff
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:dfbfe000-dfbfffff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:56:55:fb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-12-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

---

### Post by 2Mobile on 2011-10-25
"No proprietary drivers are in use on this system."

That's what I get when I look for additional drivers

---

### Post by 2Mobile on 2011-10-26
Thought I would also mention that no routers appear in the list either, even though 2 other computers in the house are hooked up to them and are working fine.

---

### Post by 2Mobile on 2011-10-26
I just got done speaking to Broadband and they said they could not help me with drivers since I am running Ubuntu. Do companies think lowly of Ubuntu? She did direct me here though, so maybe they are trying to help.

---

### Post by TBABill on 2011-10-26
```
sudo apt-get install b43-fwcutter
``` and then go to system>administration>hardware drivers and activate the b43, then restart. You'll need to be connected to the net to pull in the driver and firmware via ethernet.
 
Looks like you have the b43 active, but probably not the firmware. Following the steps above should care for the whole process for you.

---

### Post by 2Mobile on 2011-10-26
I got you till system>administration>hardware drivers.

I did a search and found system settings and in system settings I found additional drivers. Is this what you mean?

---

### Post by 2Mobile on 2011-10-26
!!!
I just did a stumbled on system check, while looking for hardware devices, and I discovered that my ubuntu version is now 11.4. I don't understand. I know for sure the live cd I installed this ubuntu from was 10.4

well other than looking stupid, which i'm pretty resigned that I do, does this change anything?

---

### Post by 2Mobile on 2011-10-26
Well, I found "Administration." Turns out, I needed to switch to Ubuntu Classic. I did what you said and now I get this when I run the terminal:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.38-8 linux-headers-2.6.38-8-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 36 not upgraded.

Once I finished, i went to drivers and, still, nothing is shown. Just a blank screen with "No proprietary driver are in use on this system"

---

### Post by 2Mobile on 2011-10-27
Does anyone have any suggestions?

---

### Post by wildmanne39 on 2011-10-27
Hi, this should do it.
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
when it is done unlug wired connection and reboot.
Thank you

---

### Post by 2Mobile on 2011-10-28
> **wildmanne39 said:**
> Hi, this should do it.
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```when it is done unlug wired connection and reboot.
Thank you

This did it! Thank you very much!

---

### Post by wildmanne39 on 2011-10-28
Hi, your welcome! would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

### Post by gulmer on 2011-10-28
what is the fwcutter for? and would this work for an rt2800usb driver?

---

### Post by gulmer on 2011-10-28
solved thanks to chili555

---

