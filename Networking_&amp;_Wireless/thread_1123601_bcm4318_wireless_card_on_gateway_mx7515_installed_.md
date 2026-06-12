---
title: "bcm4318 wireless card on gateway mx7515 installed but not detecting wireless router"
date: 2009-04-12
forum: Networking &amp; Wireless
---

### Post by jrghoull on 2009-04-12
okay i pretty much summed up the situation in the subject line. I have been searching around and trying to find out what to do but haven't found any working solutions. I have 8.10 installed, and like i said in the subject line, the wireless card seems to be installed and working, it just isn't picking up any of the nearby routers. Also, fyi, the built in modem appears to be working as well. 

I am tempted to try and see if i have the chops to try and install the ndsi wrapper since that is supposed to work better, but it seems like I am so close to getting the simplier closed sourced solution working...should i try it anyway? 

heres the lspci and iwconfig output in case it would help (i'm also posting this to show that I really have been trying to find the solution, and am coming to this as something of a last resort)

mike@linux-machine:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""
         Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
         Tx-Power=27 dBm
         Retry min limit:7   RTS thr:off   Fragment thr=2352 B
         Power Management:off
         Link Quality:0  Signal level:0  Noise level:0
         Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
         Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

mike@linux-machine:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200
(RS480/RS482/RX480/RX482) Chipset - Host bridge (rev 01)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400
AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8
[Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8
[Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8
[Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8
[Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon
Mobility X600]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036
PCI-E Fast Ethernet Controller (rev 10)
03:05.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
03:07.0 Network controller: Broadcom Corporation BCM4318 [AirForce One
54g] 802.11g Wireless LAN Controller (rev 02)
03:0e.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II
IEEE 1394 OHCI Link Layer Controller (rev 80)
mike@linux-machine:~$

anyway, if anyone knows of a post where someone has started out with a clean install of 8.10, had a 4318 card, and had used the simplier solution of installing the closed sourced version of the driver to get their card working (and have had success) please let me know.

---

