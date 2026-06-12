---
title: "Why isn't Ubuntu 9.10 picking up my wireless signal?"
date: 2010-01-25
forum: Networking &amp; Wireless
---

### Post by hawaiian1der on 2010-01-25
I installed WICD because I was looking around the internet and the Ubuntu forums said that it was the best fix for the Network Manager not working. I added the source and installed the package like the Ubuntu site said. I go to Applications => Internet => Wicd Network Manager. It says no wireless networks found. I know that the router is working because my sister is right here next to me playing Maplestory on her laptop! When I do the lshw -C network function in the terminal it is only bringing up two things: the network controller and the ethernet controller. I used Yahoo Answers as my first goto and the answers there said that Linux doesn't have the drivers for the router. I have a Netgear Wireless-N 300 Router WNR2000 and a Dell Inspiron 1750, if that helps. Can someone give me a link to the drivers or tell me in detail what to do? Please and thank you :D

---

### Post by bkratz on 2010-01-25
> **hawaiian1der said:**
> I installed WICD because I was looking around the internet and the Ubuntu forums said that it was the best fix for the Network Manager not working. I added the source and installed the package like the Ubuntu site said. I go to Applications => Internet => Wicd Network Manager. It says no wireless networks found. I know that the router is working because my sister is right here next to me playing Maplestory on her laptop! When I do the lshw -C network function in the terminal it is only bringing up two things: the network controller and the ethernet controller. I used Yahoo Answers as my first goto and the answers there said that Linux doesn't have the drivers for the router. I have a Netgear Wireless-N 300 Router WNR2000 and a Dell Inspiron 1750, if that helps. Can someone give me a link to the drivers or tell me in detail what to do? Please and thank you :D



Can you please copy/paste the output of lspci (that is LSPCI in lowercase) and what you got for the other command back here?
It is probably not the router but the interface card itself, not having drivers.

---

### Post by hawaiian1der on 2010-01-25
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

The results from the lspci command.

---

### Post by hawaiian1der on 2010-01-25
I thought I could do it with the ndiswrapper and the Wiki that goes along with it. I failed, miserably... So, if i need to uninstall it to fix my problems, please tell me what to do.

---

### Post by hawaiian1der on 2010-01-26
I went under hardware drivers. There were two there that were broadcom. I tried to activate them and it says that one was there just disabled and that he other when i tried to activate it a error came up.

---

