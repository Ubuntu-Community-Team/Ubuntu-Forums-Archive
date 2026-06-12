---
title: "Ubuntu 10.04 dont recognize any wireless network"
date: 2010-10-30
forum: Networking &amp; Wireless
---

### Post by eluis.c on 2010-10-30
I recently installed Ubuntu 10.04 in a HP Compact nc 9010 and  can't see any wireless networks. Any help??

---

### Post by eluis.c on 2010-10-30
I installed the ubuntu as the main OS. I also have the wubi version on my other laptop and dont have that problem with the wireless networks.

---

### Post by MooPi on 2010-10-31
Give us the results from ```
lspci
lsusb
```

---

### Post by eluis.c on 2010-10-31
eduardo@eduardo-laptop:~$ lspci 
00:00.0 Host bridge: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] (rev 02) 
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M] 
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02) 
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+] 
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller 
00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02) 
00:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02) 
00:0b.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50) 
00:0b.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50) 
00:0b.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51) 
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link) 
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4) 
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU] 
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller 
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M 
eduardo@eduardo-laptop:~$ lsusb 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by eluis.c on 2010-10-31
I made a mistake, its Ubuntu 10.10.

Any help here?!?!

---

### Post by eluis.c on 2010-10-31
Btw, already tried to install ndiswrapper but it says "Unable to locate package ndiswrapper"

---

### Post by MooPi on 2010-10-31
Try the drivers in Synaptic under the name bcmwl-kernel-source.
If that doesn't work follow the instructions for Broadcom chips [http://ubuntuforums.org/showthread.php?t=1604868]("http://ubuntuforums.org/showthread.php?t=1604868")

---

### Post by eluis.c on 2010-10-31
Non of them appears when I search in my Synaptic Package Manager.

---

### Post by MooPi on 2010-10-31
Your going to need to update the repository. Lets do this in terminal. ```
sudo apt-get update
```
Then try to install the drivers.

---

### Post by eluis.c on 2010-10-31
Ignore that last comment. Recently found how to connect to internet by ethernet. So im downloading things. Will let u know what happens when i finish. 

Thanks

---

