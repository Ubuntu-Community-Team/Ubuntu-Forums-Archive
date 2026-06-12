---
title: "Wireless troubleshooting: Jaunty's Broadcom 2200BG Dell inspiron 6000"
date: 2010-05-08
forum: Networking &amp; Wireless
---

### Post by croissont on 2010-05-08
Hi!
I am using Ubuntu 9.04(Jaunty) on a Dell Inspiron 6000, which has Broadcom's 2200BG wireless card.
**History**: The thing is, couple of months ago when I was using WinXP, my wireless card somehow messed up due to a malware infection. Ever since I have not been able to fix the connection. Couple of days back my OS crashed on me for the umpteenth time and I decided to shift to Linux for good. So here I am.
[B]
Present:[/B] I cannot get to fix the wireless connection at all. The situation stands thus: My card detects my modem and even though it shows the connection is established, I cannot seem to browse the internet ( I am using a CAT5 right now).
I have been reading up on all that I can find on my card/connection problems associated with it here and I have learnt much. 

I checked my logs using **dmesg** and this is what I found:
```
[   10.806841] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   10.806883] ipw2200 0000:03:03.0: firmware: requesting ipw2200-bss.fw
[   11.010303] ipw2200: Radio Frequency Kill Switch is On:
[   11.010305] Kill switch must be turned off for wireless networking to work.

```

I have the rest of the general details below.
Ubuntu 9.04 2.6.28-18-generic i686

lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
```

lsusb:
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

lsmod:
```
ipw2200               151112  0 
ieee80211              38344  1 ipw2200
```

lshw-network**(it says radio is off)**
```
  *-network:0
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:12:3f:e7:46:30
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.64 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: eth1
       version: 05
       serial: 00:13:ce:31:cc:e7
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=10.42.43.1 latency=64 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=radio off
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: c6:5f:4e:53:f5:f1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

The other thing that is being a hindrance is not being able to get the drivers of sourceforge.net.
[HTML]http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Intel_PRO/Wireless_2200BG[/HTML]
If someone can get these for me could you upload it to rapidshare or mediafire? 
I stumbled upon a topic on how to install such drivers from .exe files but can't seem to find it again. so help help! :)

cheers!

---

### Post by chili555 on 2010-05-08
It is not a Broadcom 2200BG, it is clearly an Intel. You don't need drivers, you have the correct driver ipw2200. Any driver you install is not going to work as long as the wireless switch is in the 'off' position. What does this tell us?```
rfkill list
```Do things improve if you do:```
sudo rmmod -f dell_laptop
```If this works, we can blacklist the module.

---

### Post by croissont on 2010-05-09
**rfkill list**: No manual entry for rfkill
**sudo rmmod -f dell_laptop**: ERROR: Removing 'dell_laptop': No such file or directory

I noticed it says connection established (the wireless connection), but it is greyed out and I can't seem to browse the net. Is there any other way? 
thanks for your reply chili555!

---

### Post by croissont on 2010-05-11
I have not solved this problem even now. Should it be moved to the Dell forum?

---

### Post by chili555 on 2010-05-11
> rfkill list: No manual entry for rfkillIt didn't say that. It either had some useful information or it was blank.

Unless you can find a switch or key combination that switches on the wireless, I am afraid I have no further suggestions.

---

### Post by croissont on 2010-05-12
I installed ndiswrapper couple of days back, when I had made the topic and ever since I had not changed one thing which, undoubtedly shows my noobness. I had not disconnected the ethernet cable that I had attached to my laptop from the modem. I did that today and it asked for my key..voila! My wireless works. 
I am going to restart and see if things work as they should or not.

edit: yes, it works fine. thank you UbuntuForums and chili555 for **your** time :)
 [IMG]http://www.randomfunnypicture.com/pictures/4638f475a0a48364ba25c13020ebb54aaec.jpg[/IMG]

---

