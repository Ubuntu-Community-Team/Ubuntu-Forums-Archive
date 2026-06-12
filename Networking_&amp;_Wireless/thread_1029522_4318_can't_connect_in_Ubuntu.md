---
title: "4318 can't connect in Ubuntu"
date: 2009-01-03
forum: Networking &amp; Wireless
---

### Post by weetoots on 2009-01-03
The Linksys card is WMP54GS, 14e4:4318 and works in windows.
I have read some of the other threads and tried to install the driver from the Linksys CD. I now show the driver installed, but I can get no satisfaction.
The following results are from:
sudo iwlist scan
Lspci -NN
Lshw -C network
uname -rm

doris@doris-desktop:~$ sudo iwlist scan 
[sudo] password for doris: 
lo        Interface doesn't support scanning. 

eth0      Interface doesn't support scanning. 

wmaster0  Interface doesn't support scanning. 

wlan0     Interface doesn't support scanning : Network is down 

pan0      Interface doesn't support scanning.

00:00.0 Host bridge [0600]: VIA Technologies, Inc. PT880 Ultra/PT894 Host Bridge [1106:0308] 
00:00.1 Host bridge [0600]: VIA Technologies, Inc. PT894 Host Bridge [1106:1308] 
00:00.2 Host bridge [0600]: VIA Technologies, Inc. PT894 Host Bridge [1106:2308] 
00:00.3 Host bridge [0600]: VIA Technologies, Inc. PT890 Host Bridge [1106:3208] 
00:00.4 Host bridge [0600]: VIA Technologies, Inc. PT894 Host Bridge [1106:4308] 
00:00.5 PIC [0800]: VIA Technologies, Inc. PT894 I/O APIC Interrupt Controller [1106:5308] 
00:00.7 Host bridge [0600]: VIA Technologies, Inc. PT894 Host Bridge [1106:7308] 
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8237/VX700 PCI Bridge [1106:b198] 
00:02.0 PCI bridge [0604]: VIA Technologies, Inc. PT890 PCI to PCI Bridge Controller [1106:a208] 
00:0f.0 IDE interface [0101]: VIA Technologies, Inc. Device [1106:5372] 
00:0f.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 07) 
00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev b0) 
00:10.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev b0) 
00:10.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev b0) 
00:10.3 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev b0) 
00:10.4 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 90) 
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8237S PCI to ISA Bridge [1106:3372] 
00:11.7 Host bridge [0600]: VIA Technologies, Inc. VT8251 Ultra VLINK Controller [1106:287e] 
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 7c) 
00:13.0 Host bridge [0600]: VIA Technologies, Inc. VT8237A Host Bridge [1106:337b] 
00:13.1 PCI bridge [0604]: VIA Technologies, Inc. VT8237A PCI to PCI Bridge [1106:337a] 
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV530LE [Radeon X1600/X1650 PRO] [1002:71c6] 
01:00.1 Display controller [0380]: ATI Technologies Inc RV530LE [Radeon X1650 PRO] (Secondary) [1002:71e6] 
03:06.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02) 
80:01.0 Audio device [0403]: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) [1106:3288] (rev 10) 

WARNING: you should run this program as super-user. 
  *-network               
       description: Ethernet interface 
       product: VT6102 [Rhine-II] 
       vendor: VIA Technologies, Inc. 
       physical id: 12 
       bus info: pci@0000:00:12.0 
       logical name: eth0 
       version: 7c 
       serial: 00:19:66:37:92:5f 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 latency=32 maxlatency=8 mingnt=3 module=via_rhine multicast=yes 
  *-network 
       description: Network controller 
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: 6 
       bus info: pci@0000:03:06.0 
       version: 02 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master 
       configuration: driver=b43-pci-bridge latency=32 module=ssb 
  *-network:0 DISABLED 
       description: Wireless interface 
       physical id: 1 
       logical name: wlan0 
       serial: 00:18:f8:2e:c5:92 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg 
  *-network:1 DISABLED 
       description: Ethernet interface 
       physical id: 2 
       logical name: pan0 
       serial: 4e:af:91:91:aa:75 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes 

doris@doris-desktop:~$ uname -rm 
2.6.27-7-generic i686 

 Any help will be greatly appreciated.

weetoots :confused:

---

### Post by Ayuthia on 2009-01-03
If you have a working internet connection in Ubuntu, have you tried going into System->Administration->Hardware Drivers?  You can select the Broadcom drivers from there.  If it does not show up in there, you should be able to install it by going into Synaptic and installing b43-fwcutter.

If you don't have a working connection, this link might help:
[http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72)

Hope that helps.

---

### Post by weetoots on 2009-01-03
Ayuthia,
Thanks for the reply. I don't have an Internet connect on the one machine I am working on, but I do have a connection with my other computer.

It will be awhile before I can get access to my wifes computer, then I will try the fixes you supplied.

---

### Post by melojo on 2009-01-03
That link gives you instructions without internet by using the cd.

---

### Post by acimmarusti on 2009-01-22
I got my broadcom 4318 card working in intrepid by doing the steps outlined here:

[http://ubuntuforums.org/showthread.php?t=1047297&highlight=4318](http://ubuntuforums.org/showthread.php?t=1047297&highlight=4318)

Hope it works for ya

---

