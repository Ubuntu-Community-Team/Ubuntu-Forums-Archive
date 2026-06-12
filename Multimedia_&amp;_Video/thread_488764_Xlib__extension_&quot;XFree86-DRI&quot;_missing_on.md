---
title: "Xlib:  extension &quot;XFree86-DRI&quot; missing on display &quot;:0.0&quot;. display: :0.0  screen: 0"
date: 2007-06-30
forum: Multimedia &amp; Video
---

### Post by asnd16 on 2007-06-30
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0


How can I fix this or revert to original drivers?  I think this has to do with Desktop Effects not being able to be enabled and google earth not seeing the display. ..  .

I have multiple issues in which I think are related, First Google earth does not start and gets stuck in the initialization screen or Startup splash screen, and Desktop Effects is unable to start??


Running - Ubuntu 7.04 - the Feisty Fawn
HP Pavilion dv4305us/DV4000 Notebook PC
Computer Specs -
[http://h10025.www1.hp.com/ewfrf/wc/genericDocument?cc=us&docname=c00578143&lc=en&jump](http://h10025.www1.hp.com/ewfrf/wc/genericDocument?cc=us&docname=c00578143&lc=en&jump) id=reg_R1002_USEN


Quote:
Direct Renering: NO
I have not restricted drivers on my system.

fglrxinfo
display: :0.0 screen: 0
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 915GM 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 6.5.2

After trying to re-install - [http://www.linlap.com/wiki/Configuri...UbuntuLinux704](http://www.linlap.com/wiki/Configuri...UbuntuLinux704)

I get the following -
Quote:
Xlib: extension "XFree86-DRI" missing on display ":0.0".
display: :0.0 screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

Here are related issues? [http://ubuntuforums.org/showthread.php?t=488712]("http://ubuntuforums.org/showthread.php?t=488712")
[http://ubuntuforums.org/showthread.php?t=488684]("http://ubuntuforums.org/showthread.php?t=488684")

---

### Post by asnd16 on 2007-06-30
I DONT HAVE AN ATI CARD - HERE IS 
 lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
06:05.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:06.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by tuomosi on 2007-11-11
I had same problem. Try to install older drivers. Worked fine on me.

---

