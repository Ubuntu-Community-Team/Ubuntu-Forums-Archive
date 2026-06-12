---
title: "BCM4318 does not work in Hardy"
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by childoferna on 2009-05-03
After burning no fewer than six cd's (none of which worked for installation) I bought Ubuntu Linux for Non Geeks, and installed Hardy on a Compaq Presario V6000 laptop.  Everything is working fine, I can connect to the internet and browse using ethernet.  My laptop has the BCM 4318 chipset.

I was able to install the driver using the Hardware Drivers option, then rebooted.

Now, when I click on the network manager icon in the top panel I do not see any wireless networks available.  I have tried changing the channel on my router.  

Is there further configuration I need to do?  Thanks for the help; I really want Ubuntu to work for me, but I need to have wifi on the road.

[I have attached a screenshot with some of the relevant information.]

---

### Post by RedSingularity on 2009-05-03
In terminal type "lspci" and post the output.

---

### Post by childoferna on 2009-05-03
Here are the results from lspci...

matthew@multivac:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
matthew@multivac:~$ 
matthew@multivac:~$

---

### Post by RedSingularity on 2009-05-03
There is a seven step guide for that card located [Here]("http://sampbar.com/2009/04/broadcom-bcm4318-ubuntu-intrepid/").


EDIT:  First try [this](http://ubuntuforums.org/showthread.php?t=190177).  Its much faster.

---

### Post by childoferna on 2009-05-03
The second walkthrough unfortunately points to a download no longer in existence.  

But the first one worked perfectly!  Of course, I have NO IDEA what it did, but I suppose that will come with time.

Thanks for your help, o kind Ubuntu genie

---

### Post by krazyd on 2009-05-03
Open source drivers are available for Intrepid and Jaunty - you should upgrade.

---

