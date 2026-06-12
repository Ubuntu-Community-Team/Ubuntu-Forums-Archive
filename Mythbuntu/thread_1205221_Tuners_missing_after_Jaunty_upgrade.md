---
title: "Tuners missing after Jaunty upgrade"
date: 2009-07-05
forum: Mythbuntu
---

### Post by lingenfr on 2009-07-05
My backend has three tuners #1 is a PVR-150, #2 is a PVR-USB2 and #3 is a PVR-150MCE. Today I upgraded to Jaunty. The upgrade went well except for issues with Mythexport and phpmyadmin. I was able to fix the mythexport issue later. Phpmyadmin still seems to be broken. I can't login as root and when I login as mythtv, it tells me I don't have privileges to create new databases (maybe the second part is normal). I can still login to mysql as root from the command line and can login to mythconverg as mythtv. Most phpmyadmin errors say 'Connection for controluser as defined in your configuration failed'. Everything seems to work OK with the exception of my tuners. Only #3 is recognized. Looking at dmesg and mythbackend.log I don't see any obvious errors. Here is some information:

linghome@MYTHTV-BACKEND:/var/log/mythtv$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 2040:2900 Hauppauge 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

linghome@MYTHTV-BACKEND:/var/log/mythtv$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:08.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
00:09.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]

I was going to just run mythtv-setup and check things out, but unfortunately I can't. When I connect in remotely and run mythtv-setup I get a black screen with a white outline box. I connected a monitor to my backend and I get the same black screen with a white outline box in the center. I through that it was doing its normal screen preparation and let it run quite a while, but no joy. Any assistance is appreciated, thanks.

---

### Post by lingenfr on 2009-07-07
Any help?

---

