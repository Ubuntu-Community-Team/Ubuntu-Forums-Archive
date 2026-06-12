---
title: "connecting wireless"
date: 2009-11-29
forum: Networking &amp; Wireless
---

### Post by blada4life on 2009-11-29
i have a compaq presario v5000. i had to reinstall ubuntu 9.1 becuase my computer crashed. anyway i was able to connect to my wireless network before, however i forgot how to do it. the ncsiwrapper is installed, all the proprietary drivers are installed, but when i go to the network tab at the top right of the screen it says under wireless networks that my "device not ready" i was able to fix this last time on the exact same setup. there wasnt any coding. i just want to know how to do it. here are some pictures of my current situation. oh and im using ethernet right now if it helps. [IMG]http://i880.photobucket.com/albums/ac6/maximumax1/Screenshot.png[/IMG]

---

### Post by RedSingularity on 2009-11-29
What is your lspci output?

---

### Post by blada4life on 2009-11-29
my lsawhat? haha clarify plzz (:

---

### Post by RedSingularity on 2009-11-29
Lol......in a terminal type lspci and post the output here.

---

### Post by blada4life on 2009-11-29
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

---

### Post by RedSingularity on 2009-11-29
[Here](http://ubuntuforums.org/showthread.php?t=190177) is a good guide to getting that card working.  It was written for an older ubuntu but the rules are still the same.

---

### Post by blada4life on 2009-11-29
still doesnt work

---

### Post by blada4life on 2009-11-29
the only change is now the wireless network says "wireless disabled"

---

### Post by bkratz on 2009-11-29
> **blada4life said:**
> the only change is now the wireless network says "wireless disabled"




Try this one

[http://ubuntuforums.org/showthread.php?t=1340667&highlight=BCM4318](http://ubuntuforums.org/showthread.php?t=1340667&highlight=BCM4318)

It should work

---

### Post by RedSingularity on 2009-11-29
> **bkratz said:**
> Try this one

[http://ubuntuforums.org/showthread.php?t=1340667&highlight=BCM4318](http://ubuntuforums.org/showthread.php?t=1340667&highlight=BCM4318)

It should work


Good point.  Try the fwcutter.  Its in the repositories.

---

### Post by blada4life on 2009-11-29
well that did it!
thanks for the help :KS

---

### Post by bkratz on 2009-11-29
Just one more thing to do... go to the thread tools at the top of the page and mark this [solved] to help others find it!

---

