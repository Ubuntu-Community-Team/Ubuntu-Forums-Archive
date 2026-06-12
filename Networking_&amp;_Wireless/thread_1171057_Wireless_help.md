---
title: "Wireless help"
date: 2009-05-27
forum: Networking &amp; Wireless
---

### Post by gfunkera on 2009-05-27
hey i just set up ubuntu 8.1 on my dell laptop.. everythng seems to be working fine.. the only problem is that i cant seem to connect to the wireless network that my other linux machines are connected to as well...

i am using a d-link airpro dw-ab650 wireless card... it seems to detect the network but wont connect... i click on the wireless network it attempts to connect, then it comes back asking for the password for the network and then tries for a little while then just comes back saying it disconnected....

i also have another dell wireless card but that one isnt even recognized by the OS...

any help?

---

### Post by RedSingularity on 2009-05-27
What is the output of "lspci" in the terminal?

---

### Post by gfunkera on 2009-05-27
```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 80)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:0a.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter
02:00.0 Ethernet controller: Atheros Communications Inc. AR5211 802.11ab NIC (rev 01)
```

---

### Post by RedSingularity on 2009-05-28
[Here](http://ubuntuforums.org/showthread.php?t=14442) is a similar problem.  Try the solution and see if it works.

---

