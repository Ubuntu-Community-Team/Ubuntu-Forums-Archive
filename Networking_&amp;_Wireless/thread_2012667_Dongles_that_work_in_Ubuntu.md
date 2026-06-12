---
title: "Dongles that work in Ubuntu"
date: 2012-06-29
forum: Networking &amp; Wireless
---

### Post by afhx on 2012-06-29
Members  may be interested in  this list - sorry about the formatting but it is copied from a web page([https://wiki.ubuntu.com/NetworkManager/Hardware/3G](https://wiki.ubuntu.com/NetworkManager/Hardware/3G))
   

     

                                **  [3G]("https://wiki.ubuntu.com/NetworkManager/Hardware/3G") **

                          This page is part of the [3GNetworkingIntrepid]("https://wiki.ubuntu.com/3GNetworkingIntrepid") effort. You will find information relevant for various Releases of Ubuntu, not only Intrepid. 
**Contents** 
Contents

[LIST=1]
[*] Data Card Info
[LIST=1]
[*] How to obtain device details
[*] Mobile Broadband cards
[*] Mobile Phones
[*] Provider info
[/LIST]
 
[/LIST]

  
**Data Card Info**

 This page lists hardware details and test results for mobile broadband hardware (including mobile phones) for [NetworkManager]("https://wiki.ubuntu.com/NetworkManager") 0.7 3G networking testing and development. 
If your device isn't listed, please add it to the table below. If it's not detected by the latest [NetworkManager]("https://wiki.ubuntu.com/NetworkManager") 0.7 from the [NetworkManager]("https://wiki.ubuntu.com/NetworkManager") [PPA]("http://launchpad.net/%7Enetwork-manager/+archive"), file a bug according to the instructions [here]("http://lwn.net/Articles/293813/"). **Remember to attach your lshal output to the bug report you file** and to link to the bug report from the entry for your hardware on this page. 
 
**How to obtain device details**

 Many  modems are internally installed in a laptop, or are rebranded/rebadged  devices from other providers. They also vary in terms of their  capabilities, many of which can't be discovered from the USB device IDs  alone. 
Some  detailed instructions on how to probe your modem to find out the real  manufacturer details, modem capabilities, USB vendor and product IDs,  etc can be found in [NetworkManager/Hardware/3G/Probing]("https://wiki.ubuntu.com/NetworkManager/Hardware/3G/Probing").  Adding this information - particularly the capabilities string and the  real manufacturer - to the "Notes" section of the entry for your device  would be helpful. 
 
**Mobile Broadband cards**

 For mobile phones, see the next section. This list is for add-in or built-in dedicated mobile broadband modems. 
   **Hardware** 
    **Type** 
    **Status** 
    **Provider(s)** 
    **LP Bug** 
    **Device ID** 
    **Notes** 
     Bandrich Bandluxe C100 (HSDPA) 
    USB 
    UNKNOWN 
    

   

   

   

    Bandrich Bandluxe C100S (HSDPA) 
    USB 
    works out of box 
    [ChungHwa]("https://wiki.ubuntu.com/ChungHwa") Telecom (Taiwan), Taiwan Mobile (Taiwan) 
     

    

   wvdial works fine 
     Bandrich Bandluxe C120 (HSDPA) 
    USB 
    works out of the box 
    

   

   

  Not working with Network Manager. Using wvdial. Have to unmount the device storgae before connecting though. As give here [here]("http://www.ucsclodge.lk/content/how-install-barndluxe-c120-modem")
     Bandrich Bandluxe M150 (HSDPA) 
    Mini-PCI (USB) 
    UNKNOWN 
    

   

   

   

    Bandrich Bandluxe M250 (HSUPA) 
    Mini-PCI (USB) 
    UNKNOWN 
    

   

   

   

    C-motech D-50 (CDMA) 
    USB 
    UNKNOWN 
    ice.net (Sweden) 
    

   vendor=0x16d8 product=0x6803 
    

    C-motech CNU-680 (CDMA) 
    USB 
    UNKNOWN 
    ice.net (Sweden) 
    

   vendor=0x16d8 product=0x6803 
    

    Dell 5510 Mobile Broadband (HSDPA) 
    Mini-PCI (USB) 
    Works with Network Manger & pppd 
    AT&T 
    

   vendor=0x413c product=0x8137 
    Novatel Wireless Expedite 
     Dell 5520 Mobile Broadband (HSDPA) 
    Mini-PCI (USB) 
    Works with patch to drivers/usb/serial/option.c and change to hal FDI config 
    Telstra (Australia) 
    [262498]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/262498") 
    vendor=0x413c product=0x8138 
    Novatel Wireless Expedite EU870D [MiniCard]("https://wiki.ubuntu.com/MiniCard"). AT+GCAP: +CGSM,+DS,+ES 
     Dell 5720 VZW Mobile Broadband (EVDO Rev-A) 
    Mini-PCI (USB) 
    works out of box 
    Verizon 
    

   vendor=0x413c product=0x8133 
    Novatel Wireless Expedite 
     Dell 5720 Sprint Mobile Broadband (EVDO Rev-A) 
    Mini-PCI (USB) 
    unknown 
    Sprint 
    

   vendor=0x413c product=0x8134 
    Novatel Wireless Expedite. Just change line  233 of /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi from  <match key="@info.parent:usb.product_id"  int_outof="0x8114;0x8117;0x8128;0x8129;0x8133"> to <match  key="@info.parent:usb.product_id"  int_outof="0x8114;0x8117;0x8128;0x8129;0x8133;0x8134"> and reboot.  Then everything works. 
     Ericsson F3507g Mobile Broadband Minicard 
    Mini-PCIE (USB) 
    Works with wvdail 
    Vodafone (D2) 
    [334964]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/334964") 
    vendor=0x0bdb product=0x1900 
    nm detects it, but looks like nm is not able to use it 
     Haier CE100 (EVDO Rev-A) 
    USB 
    REQUIRES HACK 
    Smart (Indonesia) 
    

   vendor=0x201e product=0x2009 
    Must eject the USB Mass Storage first, then  need either modprobe usbserial or patching option.ko. Network Manager  does not work. wvdial, pon, gnome-ppp all work fine when configured  properly. 
     HP ev2210 (EVDO Rev-A) 
    Mini-PCIE (USB) 
     

   Verizon (USA) 
    [511066]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/511066") 
    vendor=0x03f0 product=0x211d 
    Module is Sierra MC5725 
     HP hs2300 (HSDPA) 
    Mini-PCIE (USB) 
    Works with Network Manager & pppd 
    Vodafone (D2) 
    

   vendor=0x03f0 product=0x1e1d 
    Module is a Sierra MC8775, use Driver from  sierra wireless. You need to load usbserial with options vendor and  product - If Module is not visible in lsusb you need to go to windows  and enable the device in hp wireless settings 
     Huawei B81 (HSDPA) 
    USB 
    works out of box 
    M-Budget (Switzerland) 
    

   vendor=0x12d1 product=0x1446 
    same device as Huawei E1762 
     Huawei E160 (HSDPA) 
    USB 
    Works fine when connected 
    Orange (Austria), Wind (Italy), T-Mobile (UK), O2 PAYG (UK), Safaricom (Kenya) Finland
    

   

   

    Huawei E160G (HSDPA) 
    USB 
    works out of box 
    3 (UK) 
    

   vendor=0x12d1 product=0x1003 
    Detected as E220/E270 
     Huawei E166 (HSDPA) 
    USB 
    UNKNOWN 
    

   

   

   

    Huawei E169 (HSDPA) 
    USB 
    works out of box 
    Optus (Australia), Drei (Austria), O2 (Germany), [ChungHwa]("https://wiki.ubuntu.com/ChungHwa") Telecom (Taiwan), Play (Poland), Wind (Italy) 
    

   vendor=0x12d1 product=0x1001 
   Identified as Huawei E620 (same vendor and product-id) 
     Huawei E169u (HSDPA) 
    USB 
    works on 10.10+ 
    [ChungHwa]("https://wiki.ubuntu.com/ChungHwa") Telecom (Taiwan) 
    

   vendor=0x12d1 product=0x1436 
     

    Huawei E169G (HSDPA) 
    USB 
    works out of box 
    Kanguru (Portugal) 
    

   vendor=0x12d1 product=0x1001 
    This is seams to be the same device as E169 
     Huawei E170 (HSUPA) 
    USB 
    works out of box 
    

   

   

   tested with Ubuntu 8.10 and [NetworkManager]("https://wiki.ubuntu.com/NetworkManager") 0.7 
     Huawei E1762 (HSDPA) 
    USB 
    works out of box 
    M-Budget (Switzerland) 
    

   vendor=0x12d1 product=0x1446 
    

    Huawei E180 (HSUPA) 
    USB 
    works 
    Orange (Austria), 3 (Sweden) 
    

   vendor=0x12d1 product=0x1003 
    you have to blacklist airprime, which is  loaded wrongly when plugging in and won't onload anymore, so you need to  reboot in that case. UPDATE: the airprime driver has been removed in  2.6.27, so this won't be a problem in future. Identified as Huawei E220  (same vendor and product-id). Works out of the box at 3 Sweden, but may  have to manually set DNS servers 
     Huawei E180v (?) 
    USB 
    works with wvdial 
    Swisscom (Switzerland) 
    

   vendor=0x12d1 product=0x140c 
    tested with Ubuntu 9.04, wvdial works like described [here]("https://wiki.ubuntu.com/NetworkManager/Hardware/3G/Probing"), but "Stupid Mode = 1" should be added to wvdial.conf 
     Huawei E200 (HSDPA) 
    USB 
    works out of box 
    N/A 
    

   

   

    Huawei E216 (HSDPA) 
    USB 
    UNKNOWN 
    

   

   

   

    Huawei E219 (HSDPA) 
    USB 
    works out of the box 
    [DiGi]("https://wiki.ubuntu.com/DiGi") (Malaysia) 
    

   vendor=0x12d1 product=0x1003 
    tested with Ubuntu 9.04 and [NetworkManager]("https://wiki.ubuntu.com/NetworkManager") 0.7 
     Huawei E220 (HSDPA) 
    USB 
    works out of box 
    Tele2 Sweden, 3 Sweden, Orange (Austria), Play  (Poland), Vodafone (Spain), 3 Italia, e-mobile (Japan), Telenor  (Serbia), Safaricom (Kenya) 
    

   vendor=0x12d1 product=0x1003 
    in Japan, e-moble sells it as "D02HW";   "Out of box", on Eee 1000HD, only with "network-manager" & eee kernel ([http://array.org/ubuntu/](http://array.org/ubuntu/)) 
     Huawei E226 (HSDPA) 
    USB 
    Works 
    Claro (Brazil) 
    

   vendor=0x12d1 product=0x1003 
    Have to manually edit the DNS servers in /etc/resolv.conf, ADD nameserver 200.255.121.39  nameserver 200.169.117.14 
     Huawei E230 (HSUPA) 
    USB 
    works out of the box 
    3 Austria, MTN South Africa 
    

   

   Recognized as E220. 
     Huawei E270 (HSUPA) 
    USB 
    Works 
    3 Sweden 
    

   

   I have "blacklist airprime" in  /etc/modprobe.d/blacklist for my E220. UPDATE: the airprime driver has  been removed in 2.6.27, so this won't be a problem in future. 
     Huawei E510 (HSDPA) 
    USB 
    UNKNOWN 
    

   

   

   DVB-T Mobile TV 
     Huawei E620 
    USB 
    NOT WORKING (with NM 0.7)/ works (NM 0.7.1~rc4) 
    PT Kanguru, simyo 
    [270282]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/270282") 
    vendor=0x12d1 product=0x1001 
    PCMCIA card identified as USB device, internal modem in eeePC 901go 
     Huawei E620 
    USB 
    Works 
    three.ie 
          [546728]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546728/") 
    vendor=0x12d1 product=0x1001 
   In lucid, needs  usb-modeswitch-data_20100127-1_all.deb and  usb-modeswitch_1.1.0-2_i386.deb installing and probably sudo modprobe  option  
     Huawei E870  
    USB/EXPRESSCARD  
    Works out of box  
     T-Mobile Austria  
     

   vendor=0x12d1 product=0x1003 
     web'n'walk [ExpressCard]("https://wiki.ubuntu.com/ExpressCard") IV; is identified as E220; Ubuntu 8.10 + NM 0.7  
     Huawei E1550 
    USB 
    Works  
    Zain/Celtel (Kenya), drei (Austria) 
    [401655]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/401655") 
    vendor=0x12d1 product=0x1001 
    Works in Karmic but not Jaunty. Works in Lucid only with usb-modeswitch installed. 
     Huawei E1750 (HSPA) 
    USB 
    Works 
    Safaricom (Kenya), Mobitel (Sri Lanka), available in open market 
    

   vendor=0x12d1 product=0x1446 
    Works out of the box in Maverick (tested with  kernel 2.6.35-7). Lucid (2.6.32-24) works with usb-modeswitch installed.  Modem is also network-locked 
     Huawei E1752 (HSDPA) 
    USB 
    Works 
    Telenor (Denmark) 
    

   vendor=0x12d1 product=0x1001 
    Works in Lucid (2.6.32-25) with usb-modeswitch installed. 
     Huawei EC121 (CDMA2000) 
    USB 
    UNKNOWN 
    

   

   

   

    Huawei EC168 (EVDO Rev-A) 
    USB 
    works in 9.10 
    Alltel USA 
    

   

   Works with network manager out of the box.  Just type in info and set to connect automatically 
     Huawei EC168C  
    USB 
    Detected but does not work in Karmic 
   Reliance (India) 
    [478529]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/478529") 
    vendor=0x12d1 product=0x1412 
   Works fine in Jaunty, In Karmic using Wvdial 
     Huawei EC226 (EVDO Rev-A) 
    USB 
    Works (in Lucid works with wvdial) 
    CAT Telecom Thailand/Orange Kenya 
    

   vendor=0x12d1 product=0x1001 
    In Lucid, shows up in [NetworkManager]("https://wiki.ubuntu.com/NetworkManager") 0.8.1 but cannot connect even with correct settings. But with wvdial works straightforward. Doesn't need usb-modeswitch 
     Huawei EC321 (CDMA2000) 
    PCMCIA 
    UNKNOWN 
    

   

   

   

    Huawei EC325 (CDMA2000) 
    USB 
    UNKNOWN 
    

   

   

   

    Huawei EC328 (CDMA2000) 
    USB 
    UNKNOWN 
    

   

   

   

    Huawei EC360 (EVDO Rev-0) 
    PCMCIA 
    UNKNOWN 
    

   

   

   

    Huawei EC500 (EVDO Rev-A) 
    PCMCIA 
    UNKNOWN 
    

   

   

   

    Huawei EC821 (CDMA2000) 
    PCMCIA 
    UNKNOWN 
    

   

   

   

    Huawei EC1260 (HSD Rev-A) 
    USB 
    Detected but does not work in Karmic 
    Reliance (India) 
    [446146]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146") 
    vendor=0x12d1 product=0x140b 
    Works fine in Jaunty 
     Huawei EG162G (EDGE) 
    USB 
    UNKNOWN 
    

   

   

   

    Huawei EG602 (EDGE) 
    PCMCIA 
    UNKNOWN 
    

   

   

   

    Huawei K3520 (HSDPA) 
    USB 
    Brick 
    Vodafone (South Africa) 
    [https://bugs.launchpad.net/bugs/598555](https://bugs.launchpad.net/bugs/598555) 
    12d1:1001 
    

    Huawei K3765 (HSDPA) 
    USB 
    works on 10.04 after modeswitch 
    Vodafone (Australia) 
    [http://ubuntuforums.org/showthread.php?t=1465557](http://ubuntuforums.org/showthread.php?t=1465557) 
    ID 
    install usb-modeswitch. 
     HUAWEI Mobile 
    USB 
    Works in 10.10 
    Telefónica O2 (CZ) 
    

   12d1:1406 
    

 
||  IPWireless, Inc. UMTS-TDD (TD-CDMA) modem || USB || Must be connected  during boot, otherwise not detected by network manager. Cannot connect  anyway. || T-Mobile CZ || || 0bc3:0001 || +GCAP:  +CBC,+CGDCONT,+CLCK,+CMEE,+COPS,+CPOST,+CSQ,+IPR +COPS: 1,2,"23001"  +CREG: 0,1 Can connect under root with: #!/bin/bash /usr/sbin/pppd  /dev/ttyUSB0 user gprs password gprs updetach defaultroute usepeerdns  connect '/usr/sbin/chat -e ABORT BUSY ABORT "NO CARRIER" ABORT  "AUTHENTICATION FAILURE" "" ATZ OK  "AT+CGDCONT=1,\"PPP\",\"internet.t-mobile.cz\",\"0,0\",0,0" OK ATD*99#  CONNECT' || 
   LG LDU-1900D EVDO Rev.A 
    USB 
    Works after modeswitch 
    Wana (Morocco) 
    - 
    vendor=0x1004 product=0x6107 
   Use usb_modeswitch to transform PID 0x1000 into 0x6107. 
     MU-Q101 
    USB 
    modem not detected, only usb-storage detected and loaded 
    

   [259028]("https://bugs.edge.launchpad.net/ubuntu/+source/network-manager/+bug/259028") 
    vendor=0x0408 product=0xea02 
    Init with ATE0V1&D2&[C1S0]("https://wiki.ubuntu.com/C1S0")=0 
     Novatel Wireless Expedite E725 (EVDO Rev-A) 
    USB-MiniPCIE 
    UNKNOWN 
    

   

   

   

    Novatel Wireless Expedite EU850D (HSDPA) 
    USB-MiniPCIE 
    UNKNOWN 
    

   

   

   

    Novatel Wireless Expedite EU860D (HSDPA) 
    USB-MiniPCIE 
    UNKNOWN 
    

   

   

   

    Novatel Wireless Expedite EU870D (HSDPA) 
    USB-MiniPCIE 
    UNKNOWN 
    

   

   vendor=0x413c product=0x8138 
    

    Novatel Wireless Merlin U630 (UMTS) 
    PCMCIA 
    Is not seen by network manager 
    Kanguru (Portugal) 
    [248630]("https://bugs.edge.launchpad.net/ubuntu/+source/network-manager/+bug/248630") 
    vendor=0x00a4 product=0x0276 
    Requires module serial_cs. To work with full  bandwidth requires the command: "/bin/setserial <device, usually  /dev/ttyS0> spd_warp low_latency" 
     Novatel Wireless Merlin U740 (HSDPA) 
    USB/PCMCIA 
    UNKNOWN 
    

   

   

   

    Novatel Wireless Merlin PC720 (EVDO Rev-A) 
    USB/PCMCIA 
    UNKNOWN 
    

   

   

   

    Novatel Wireless Merlin X720 (EVDO Rev-A) 
    USB/EXPRESSCARD 
    Works out of the box 
    Verizon (USA) 
    

   vendor=0x1410 product=0x1120 
    +GCAP: +CIS707-A, CIS-856-A, +MS, +ES, +DS 
     Novatel Wireless Merlin X950D (HSUPA) 
    USB/EXPRESSCARD 
    UNKNOWN 
    

   

   

   

    Novatel Wireless Merlin XU870 (HSDPA) 
    USB/EXPRESSCARD 
    UNKNOWN 
    

   

   

   

    Novatel Wireless Merlin XV620 (EVDO Rev-A) 
    USB/EXPRESSCARD 
    UNKNOWN 
    

   

   

   

    Novatel Wireless Ovation MC727 (EVDO Rev-A) 
    USB 
    UNKNOWN 
    

   

   

   

    Novatel Wireless Ovation MC760 
    USB 
    Works out of the box 
    Virgin Mobile [BroadBand2Go]("https://wiki.ubuntu.com/BroadBand2Go") 
    

   vendor=0x1410 product=0x0531 / 0x6002 
    Switches product id to 6002 after eject of  storage, then can be configured using network manager.  Device must  first be activated using WinXP or similar (on-device, windows-only  configuration software) 
     Novatel Wireless Ovation MC930D (HSUPA) 
    USB 
    Detected as storage, eject /dev/srX is enough to switch to ttyUSB (option) mode 
    O2 (uk) 
    

   ID 1410:4400 Novatel Wireless 
    

    Novatel Wireless Ovation MC950D (HSUPA) 
    USB 
    Detected out of the box with 8.04 and NM 0.7 but dialing fails. wvdial works 
    

   

   idVendor=0x1410 idProduct=0x4400 
    +CGSM,+DS,+ES 
     Novatel Wireless Ovation MC950D (HSUPA) 
    USB 
    9.10 (Karmic): Detected as storage, ejecting  /dev/srX is enough to switch to ttyUSB (option) mode. Dialing with NM  0.7.996 works fine! 
   Provider: [HELLO]("https://www.hello.com.kh/")(Cambodia) 
    

   idVendor=0x1410 idProduct=0x4400 
    [[http://www.novatelwireless.com/index.php?option=com_content&view=article&id=176&Itemid=331|Novatel]("http://www.novatelwireless.com/index.php?option=com_content&view=article&id=176&Itemid=331%7CNovatel"): Linux Setup Guide]] 
     Novatel Wireless Ovation MC990D (HSPA) 
    USB 
    Detected out of the box with 9.04 and NM 0.7.0.1 but dialing fails. wvdial and gnome-ppp works  
   Movistar (Spain)
    

  vendor=0x1410 product=0x7001
    

    Novatel Wireless Ovation MC990D (HSPA) (Model NRM-MC990D) 
    USB 
    After following tweaks in "Notes" to get device recognized, Network Manager wizard was able to connect up flawlessly in 9.10 
   Vodacom (Mozambique)
    

  vendor=0x1410 product=0x0520
   Had to use the Instructions here to load the device ([[http://www.novatelwireless.com/index.php?option=com_content&view=article&id=176&Itemid=331](http://www.novatelwireless.com/index.php?option=com_content&view=article&id=176&Itemid=331)]), then the "Eject" trick here ([[http://www.draisberghof.de/usb_modeswitch/#hardware](http://www.draisberghof.de/usb_modeswitch/#hardware)])  to get device detected.  Sometimes you have to wait 10 mins for Gnome  to give up trying to automount before Eject will be allowed.
     Novatel Wireless Ovation MCD3000 (EVDO Rev-A) 
    USB 
    UNKNOWN 
    

   

   

   

    Option Wireless Globetrotter GT 0201 (HSDPA) 
    USB/PCMCIA 
    UNKNOWN 
    

   

   

   

    Option Wireless Globetrotter GT 0202 (HSDPA) 
    USB/PCMCIA 
    UNKNOWN 
    

   

   

   

    Option Wireless Globetrotter GT MAX 201 (HSDPA) 
    USB/PCMCIA 
    UNKNOWN 
    

   

   

   

    Option Wireless Globetrotter GT MAX 202 (HSDPA) 
    USB/PCMCIA 
    UNKNOWN 
    

   

   

   

    Option Wireless Globetrotter GT MAX HSUPA (HSUPA) 
    USB/PCMCIA 
    UNKNOWN 
    

   

   

   

    Option Wireless Globetrotter Express 7.2 (HSDPA) 
    USB/EXPRESSCARD 
    works 
    T-Mobile Austria 
    

  vendor=0x0af0 product=0x6711  
   needs ozerocdoff ([http://www.pharscape.org/forum/index.php?topic=545.0](http://www.pharscape.org/forum/index.php?topic=545.0)) Model GE0201, branded as web'n'walk expresscard II; Ubuntu 8.10 + NM 0.7 
     Option Wireless Globetrotter Express HSUPA (HSUPA) 
    USB/EXPRESSCARD 
    UNKNOWN 
    

   

   

   

    Option Wireless Globetrotter iCON 7.2 (HSDPA) 
    USB 
    almost works 
    XS4ALL (Netherlands)
    [282787]("https://bugs.edge.launchpad.net/ubuntu/+source/network-manager/+bug/282787"), 256296 & 272254 
    vendor=0x0af0 product=0x6911 
    Requires rezero (from ~martijn/ppa) or  usb_modeswitch; have to blacklist 'udev.tar.tz fromoption' driver; GSM  connection option is shown twice in n-m, but there's only one hso device  
     Option Wireless Globetrotter iCON HSUPA (HSUPA) 
    USB 
    UNKNOWN 
    

   

   

   

    Option Wireless GTM378 (HSDPA) 
    USB/Mini-PCIE 
    UNKNOWN 
    

   

   

   

    Option Wireless GTM380 (HSUPA) 
    USB/Mini-PCIE 
    Not detected by NM0.7 
    Vodafone Ireland 
    

   vendor=0x0af0 product=0x7201 
    Can be manually configured (usbserial) 
     Option Wireless GTM382 (HSUPA) 
    USB/Mini-PCIE 
    Works after some hacks 
    

   

   vendor=0x0af0 product=0x7501 
    Requires turning off ZeroCD plus some HAL tweaks; [ColinWatson]("https://wiki.ubuntu.com/ColinWatson") will push these upstream 
     Option Wireless GTM501 (HSUPA) 
    USB/Embedded 
    UNKNOWN 
    

   

   

   

    Option Wireless iCON 210 (HSDPA) 
    USB 
    is not seen by network-manager 
    MCel(Mozambique) 
    

   vendor=0x0af0 product=0x4002 (before modeswitch) product=0x4000 (after modeswitch) 
    Works with usb-modeswitch, summary: [[http://www.equilaris.at/blog/2010/01/13/icon-210-in-ubuntu-9-10/](http://www.equilaris.at/blog/2010/01/13/icon-210-in-ubuntu-9-10/)] 
     Option Wireless iCON 225 (HSDPA) 
    USB 
    works and is seen by network-manager 
    Orange(Uk) 
    

   vendor=0x0af0 product=0x6971 
    using hso-1.6.tar.gz and udev.tar.gz from pharscape. All now working with network-manager 
     Option Wireless iCON 401 (HSUPA) 
    USB 
    Works in 8.10 by using ozerocdoff. Does NOT work in 9.04 anymore
   Welho/DNA 
    

  vendor 0×0af0 product 0×7401 
    Will become to work in 9.04 when [NetworkManager]("https://wiki.ubuntu.com/NetworkManager") 0.7.1 is released or use this  [workaround]("http://ubuntuforums.org/showpost.php?p=7742081&postcount=17")  
     Option Wireless iCON 505 (HSDPA) 
    USB 
    Working with [NetworkManager]("https://wiki.ubuntu.com/NetworkManager") 0.7.0.100 in 9.04 
    3(UK) 
    

   vendor=0x0af0 product=0xd055 
    using hso-1.12.tar.gz and udev.tar.gz from  Pharscape. Disconnect button from the applet (available once connected)  doesn't work  
     Option Wireless Globetrotter (HSUPA) 
    USB/PCMCIA 
    works out of the box 
    Vodafone (germany) 
    

   

   

    Option Wireless Globetrotter GPRS (GPRS) 
    USB 
    UNKNOWN 
    

    

   vendor=0x0013 product=0x???? 
    

    Option Wireless Globetrotter Fusion (HSDPA) 
    USB 
    UNKNOWN 
    

    

   vendor=0x0af0 product=0x6000 
    

    Option Wireless Globesurfer Icon (HSDPA) 1.8mbs 
    USB 
    works with usb-storage>usb-serial switch 
    

    

   vendor=0x0af0 product=0x6600 
   Use icon_switch or usb_modeswitch tools. 
     Pantech UMW190 (EVDO Rev-A/GSM) 
    USB 
    is not seen by network-manager in Lucid 
    Verizon (USA) 
    

   vendor=106c product=3716 
    EVDO works with gnome-ppp, GSM not tested 
     Samsung Kiera internal modem (used in N150 EOM) 
    USB 
    connects sometimes good, sometimes not at all with 11.04 
     

   

   vendor=0x04e8 product=0x6872 
     

    Sierra Wireless [AirCard]("https://wiki.ubuntu.com/AirCard") 595 (EVDO Rev-A) 
    USB/PCMCIA 
    works out of box 
    N/A 
    

   

   

    Sierra Wireless [AirCard]("https://wiki.ubuntu.com/AirCard") 595U (EVDO Rev-A) 
    USB 
    works out of box 
    N/A 
    

   

   

    Sierra Wireless [AirCard]("https://wiki.ubuntu.com/AirCard") 597E (EVDO Rev-A) 
    USB/EXPRESSCARD 
    UNKNOWN 
    

   

   

   

    Sierra Wireless [AirCard]("https://wiki.ubuntu.com/AirCard") 598 (EVDO Rev-A) 
    USB 
    not yet 
    Sprint 
    

   vendor=0x1199 product=0x0025 
    must run pppd manually, [NetworkManager]("https://wiki.ubuntu.com/NetworkManager") doesn't detect it 
     Sierra Wireless [AirCard]("https://wiki.ubuntu.com/AirCard") 875 
    PCMCIA 
    works out of box 
   Orange(Austria) AT&T 
    

   

   

    Sierra Wireless [AirCard]("https://wiki.ubuntu.com/AirCard") 880 (HSUPA) 
    USB/CARDBUS 
    UNKNOWN 
    

   

   

    European Optimised Version of the 881 
     Sierra Wireless [AirCard]("https://wiki.ubuntu.com/AirCard") 880E (HSUPA) 
    USB/EXPRESSCARD 
    works out of box - used umtsmon to connect 
    

   

   

    European Optimised Version of the 881E 
     Sierra Wireless [AirCard]("https://wiki.ubuntu.com/AirCard") 880U (HSUPA) 
    USB 
    works out of the box 
    AT&T 
    

   vendor=0x1199 product=0x6856 
     European Optimised Version of the 881U, assumed to be the same status 
     Sierra Wireless [AirCard]("https://wiki.ubuntu.com/AirCard") 881 (HSUPA) 
    USB/CARDBUS 
    works with Sierra homepage instructions 
    AT&T 
    

   vendor=0x1199 product=0x6851 
    [NetworkManager]("https://wiki.ubuntu.com/NetworkManager") does not control the device, fails setting APN, has to be controlled via external pppd w/sierra ppp gsm scripts  
     Sierra Wireless [AirCard]("https://wiki.ubuntu.com/AirCard") 881E (HSUPA) 
    USB/EXPRESSCARD 
    UNKNOWN 
    

   

   

   

    Sierra Wireless [AirCard]("https://wiki.ubuntu.com/AirCard") 881U (HSUPA) 
    USB 
    works out of the box 
    AT&T 
    

   vendor=0x1199 product=0x6856 
     have to manually load the "option" driver, [NetworkManger]("https://wiki.ubuntu.com/NetworkManger") won't control the connection have to manually run "pppd" 
     Sierra Wireless [AirCard]("https://wiki.ubuntu.com/AirCard") 885E (HSUPA) 
    USB/EXPRESSCARD 
    UNKNOWN 
    

   

   

   

    Sierra Wireless Apex 880 (HSUPA) 
    USB 
    UNKNOWN 
    N/A 
    

   

   

    Sierra Wireless Compass 597 (EVDO Rev-A) 
    USB 
    UNKNOWN 
    N/A 
    

   

   

    Sierra Wireless Compass 885 (HSUPA) 
    USB 
    UNKNOWN 
    AT&T 
    

   vendor=0x1199 product=0x6880 
    +GCAP: +CGSM,+FCLASS,+DS +COPS: 0,0,"ATT@",0 
     Sierra Wireless MC5725 (EVDO Rev-A) 
    USB/Mini-PCIE 
    UNKNOWN 
    

   

   

   

    Sierra Wireless MC5725V (EVDO Rev-A) 
    USB/Mini-PCIE 
    UNKNOWN 
    

   

   

   

    Sierra Wireless MC8775 (HSDPA) 
    USB/Mini-PCIE 
    works, but required some tweaking 
    O2 (UK), Elisa Finland 
    See [SierraMC8775]("https://wiki.ubuntu.com/SierraMC8775") 
    vendor=0x1199 product=0x6813 
    

    Sierra Wireless MC8775V (HSDPA) 
    USB/Mini-PCIE 
    UNKNOWN 
    

   

   

   

    Sierra Wireless MC8780 (HSUPA) 
    USB/Mini-PCIE 
    UNKNOWN 
    

   

   

   

    Sierra Wireless MC8781 (HSUPA) 
    USB/Mini-PCIE 
    UNKNOWN 
    

   

   

   

    Sierra Wireless MC8785V (HSUPA) 
    USB/Mini-PCIE 
    UNKNOWN 
    

   

   

   

    Sierra Wireless MC8790 (HSUPA) 
    USB/Mini-PCIE 
    UNKNOWN 
    

   

   

   

    Sierra Wireless MC8790V (HSUPA) 
    USB/Mini-PCIE 
    UNKNOWN 
    

   

   

   

    Sony Ericsson GC86 (EDGE) 
    PCMCIA 
    

   

   

   

   

    Vodafone K3565 
    USB 
    works out of the box (9.04) but doesn't always appear to provide DNS servers via DHCP 
    Vodafone (UK) 
    

   vendor=0x12d1 product=0x1003 
    Similar to Huawei E160G, but no external antenna socket 
     Vodafone K3565-Z 
    USB 
    works out of box (10.10) 
    Vodafone (de) 
    

   vendor=0x19d2 product=0x0063 
    Manufactured by ZTE. Perhaps usb_modeswitch  necessary (see ZTE MF636+). CD-Mode has Product-ID 0x2000. Takes long  time (1min) for detection 
     Vodafone Mobile Connect Original (UMTS) 
    PCMCIA 
    UNKNOWN 
    

   

   vendor=0x1045 product=0xc861 
    

    Vodafone Mobile Connect, UK (Merlin UMTS Modem) 
    PCMCIA 
    not seen by network manager 
    N/A 
    [248630]("https://bugs.edge.launchpad.net/ubuntu/+source/network-manager/+bug/248630") 
    vendor=0x00a4 product=0x0276  
    

    ZTE MF190 
    USB 
    Works (Read notes) 
    Cell C (South Africa) 
    

   vendor=0x19d2 product=0x1224 (before) product=0x0082 (after) 
    If you have trouble switching, so that the  ports show, just eject the "CD" drive that mounts. the device then  switches. In Lucid, [NetworkManager]("https://wiki.ubuntu.com/NetworkManager")  does not see the device after switching. Try wvdial. In Maverick and  Natty, after switching, follow the New Connection wizard and you'll be  ok. 
     ZTE MF330 
    PCMCIA 
     

   Orange (Poland) 
    

    vendor=0x19d2 product=0x0001 
    Works with wvdial&comgt, not detected by NM, reported [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/501005](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/501005) 
     ZTE MF627 (HSDPA) 
    USB 
    Works after workarounds (usb_modeswitch + HAL FDI) 
    3 (UK), Smart (Philippines) 
    [310025]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/310025") FDI attached to: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/310025](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/310025) 
    vendor=0x19d2 product=0x0031 
     

    ZTE MF628 (HSDPA) 
    USB 
    works, if driver detected correctly(product=0x0015) 
    Yesss (Austria) 
    [269858]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/269858") FDI attached to: [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/267727](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/267727) 
    vendor=0x19d2 product=0x0015 
    In 2.6.27: usb-storage patch  
     ZTE MF636+ 
    USB 
    Works after usb_modeswitch 
    Elisa, Sonera / Finland, Cosmote (Greece) 
    

   Vendor=0x19d2 Product=0x2000 
    usb_modeswitch target ID's: Vendor=0x19d2 Product=0x0031 
     ZTE CDMA (ONDA Communication S.p.A.) 
    USB 
    UNKNOWN
    Reliance Broadband(India) 
    

    vendor=0x19d2 product=0xfffd 
    Works properly with usbserial 
  
||  BSNL's EVDO Card "Prithvi"|| USB || Not able to connect though  recognizable as mass storage and CD storage and  listing in Network  Manager || BSNL, India || [864658]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/864658") || Bus 002 Device 018: ID 15eb(product):1231(device)   iM=1 iP=2 if=0 || NOT WORKING 
   ZTE AC8710 (CDMA/EVDO) 
    USB 
    Not recognized by [NetworkManager]("https://wiki.ubuntu.com/NetworkManager") 
    Tata Indicom Photon+ (India) 
    [384344]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/384344") 
    vendor=0x19d2 product=0xffff 
    ONDA Communication S.p.A. +GCAP: +CIS707-A,  CIS-856, +MS, +ES, +DS, +FCLASS. Works with wvdial/gnome-ppp/kppp after  manually loading usbserial. 
  
 
**Mobile Phones**

    **Hardware** 
    **Type** 
    **Status** 
    **Provider(s)** 
    **LP Bug** 
    **Device ID** 
    **Notes** 
     CECT P168+ (aka the Apple iPhone clone) 
    GSM Phone, used as GPRS Modem, internet via Bluetooth (this phone does not use USB for this) 
    Not detected NM 0.7, works via WVDial, but extremely complicated to get it to work 
    All Providers (Poland) 
    293846 
    gsmctl -d <MEO0> Manufacturer: MTK1  <ME1> Model: MTK2 <ME2> Revision:  YG718-03-SIV100ASIV100B-IPHON, 2007/11/29 18:52 <ME3> Serial  Number: 354969010811212>
    Can't find device ID 
     Nokia 3109c 
    GSM Phone via USB 
    not detected 
    

   [259041]("https://bugs.edge.launchpad.net/ubuntu/+source/hal-info/+bug/259041") (proposed fix uploaded to [NetworkManager PPA]("https://edge.launchpad.net/%7Enetwork-manager/+archive"))
    

   

    Nokia 5800 
    GSM/UMTS Phone via USB/Bluetooth 
    USB is detected/enabled automatically (nm-0.7), Bluetooth works after a small edition as detailed in [*NetworkManager/Hardware/3G/Probing]("https://wiki.ubuntu.com/NetworkManager/Hardware/3G/Probing") 
    DNA Finland 
    

   

   

    Nokia 6300 
   GSM Phone via USB 
    Needs a small patch to hal-info (nm-0.7) 
   MTN Nigeria 
    [258197]("https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/258197") (Works out of the box with hal-info from [NetworkManager PPA]("https://edge.launchpad.net/%7Enetwork-manager/+archive"))
    

   

    Nokia 6120c 
    GSM/UMTS Phone via USB 
    Works out-of-box 
    3 UK 
    

   

   

    Nokia 6500c 
    GSM Phone via Bluetooth 
    Not detected, works fine with manual configuration 
    Vodafone Ireland 
    

   

   

    Nokia 6500c 
    GSM Phone via USB 
    Works fine 
    Most providers, KPN Netherlands in this case. 
    

   vendor=0x0421, product=0x003d; +GCAP: +CGSM,+DS,+W 
    

    Nokia 6630 
   GSM/UMTS Phone via USB/Bluetooth 
    Detected via USB / Not detected via Bluetooth 
   Saunalahti (Finland) 
     

   vendor=0x0421, product=0x0410 
    Tested with DKU-2, CA-52 - both work 
     Nokia E51 
   GSM/UMTS Phone via USB/Bluetooth 
    Not detected via USB 
   Swisscom (Switzerland) 
    [261416]("https://launchpad.net/bugs/261416") 
    

   

    Nokia E75 
   GSM/UMTS/HSDPA Phone via USB/Bluetooth 
    Detected via USB / Not detected via Bluetooth 
    E-Plus Germany 
    [https://bugs.launchpad.net/network-manager/+bug/262392](https://bugs.launchpad.net/network-manager/+bug/262392) 
    

   freezes Ubuntu Karmic Koala upon attempt to reconnect 
     Nokia E71 
   GSM/UMTS/HSDPA Phone via USB/Bluetooth 
    USB modem works out of the box, Bluetooth 
   E-Plus (Germany), Telkomsel Flash (Indonesia) 
    [#257045]("https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/257045") 
    vendor=0x421, product=0xab 
    Using Kubuntu Intrepid Ibex 8.10 with latest updates. Bluetooth may need [BlueMan]("https://wiki.ubuntu.com/BlueMan") 
     Nokia E70 
   GSM/UMTS Phone via USB/Bluetooth 
    Detected via USB / Not detected via Bluetooth 
   o2 (Germany) 
    [257725]("https://bugs.launchpad.net/bugs/257725") (proposed fix uploaded to [NetworkManager PPA]("https://edge.launchpad.net/%7Enetwork-manager/+archive"))
    

   

    Nokia E90 
    GSM/UMTS Phone via USB/Bluetooth 
    Not detected by NM, but works fine with manual rfcomm+pppd+chat setup.  
    TDC/Sonofon (Denmark) 
    [274952]("https://bugs.edge.launchpad.net/ubuntu/+source/network-manager/+bug/274952") 
     +GCAP: +CGSM,+DS,+W +COPS: 0,2,"23801",2  <ME0>  Manufacturer: Nokia <ME1>  Model: Nokia E90  <ME2>  Revision: V 210.41.48.2 10-04-08 RA-6 (c) Nokia <ME3>   Serial Number:xxx vendor=0x421 product=0x04ce
    Solution is described in the bug 
     Nokia E90 
    GSM/UMTS Phone via USB/Bluetooth 
    Works fine 
    Saunalahti (Finland) 
     

    

   Using Ubuntu Lucid. Getting Bluetooth working required blueman-manager (from blueman package) 
     Nokia N73 
    GSM/UMTS/HSDPA phone via Bluetooth 
    Not detected, works fine with manual configuration 
    Vodafone (Spain) 
    

   

   

    Nokia N73 
    GSM/UMTS/HSDPA phone via USB 
    Detected, works great 
    Orange (Romania) 
    

   

   

    Nokia N82 
    GSM/UMTS/HSDPA phone via USB 
    Works out of the box 
    All 
    

   

   Works fine in both Karmic and Lucid. Just connect phone in PC Suite Mode 
     Nokia N85 
    GSM/UMTS/HSDPA phone via Bluetooth/USB 
    "Detected" by NM, connection attempts may fail  due to wrong default AP: 0 add device ID to  /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi Nokia section 1  configure mobile broadband using Comviq/Tele2, 2 change connection APN  from "mobileinternet.tele2.se" to "internet.tele2.se" i.e. default  received in cfg messages from comviq. 
    Comviq/Tele2 Sweden.  
    

   ID 0421:0094 
    connects fine via wvdial when specifying tele2's internet.tele2.se as AP, and forcing the nameservers into resolve.conf 
     Nokia N900 
    GSM/UMTS/HSDPA phone via USB 
    "Detected" by NM, in pc connectivity mode 
    Wind (Canada) 
    

   ID 0421:01c8 
    

    Nokia N95-2 
    GMS/UMTS/HSDPA phone via USB 
    Generic CDC+ACM, Works after small hal-info patch 
    T-Mobile (UK) 
    [bug 285494]("https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/285494") 
    vendor=0x0421, product=0x070 
    

    Nokia N95-3 (RM-160) 
    GSM/UMTS/HSDPA phone via USB 
    Generic CDC+ACM, Works after small hal-info patch  
    Telstra (Australia) 
    [bug 262556, with patch]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/262566") 
    vendor=0x0421, product=0x04f0, AT+GCAP: +GCAP: +CGSM,+DS,+W 
    

    Nokia N95-3 (RM-160) 
    GSM/UMTS/HSDPA phone via Bluetooth 
    Not detected via bluetooth, but works fine with manual rfcomm+pppd+chat setup. 
    Telstra (Australia) 
    

   

   

    T-Mobile Dash 
    GSM Phone via USB 
    generic rndis device 
    T-Mobile(USA) 
    

   

   

    Toshiba TS705 
    GSM Phone via USB 
    Detected, not able to connect yet 
    Yoigo (Spain)
    [255304]("https://launchpad.net/bugs/255304") and [257111]("https://launchpad.net/bugs/257111") 
    

   

    LG U990 
    GSM/UMTS/HSDPA phone via USB 
    Generic CDC+ACM, works after small hal-info patch 
    Three (Australia) 
    [263044]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/263044") 
    vendor=0x1004, product=0x6000 
    

    LG U990 
    GSM/UMTS/HSDPA phone via Bluetooth 
    Not detected by NM, but works fine with manual rfcomm+pppd+chat setup 
    Three (Australia) 
    

   AT+GCAP: +CGSM,+DS,+ES 
    

    RIM [BlackBerry]("https://wiki.ubuntu.com/BlackBerry") 8100 
    CDMA Phone via USB/Bluetooth 
    Not detected by NM, works fine whit KPPP 
    Iusacell(México) 
    [290576]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/290576") 
    vendor=0fca, product=0004 Research In Motion, Ltd. 
    

    Samsung SGH-Z370 
    GSM/UMTS phone via USB/Bluetooth 
    works out-of-box 
    Play (Poland) 
    

   vendor=0x04e8, product=0x6601 
    Detected as Samsung Z100 via USB, plays well with NM0.7 via USB, for bluetooth use command line 
     Sony Ericsson K510i 
    GSM/EDGE phone via USB/Bluetooth 
    Works out-of-box 
    Telkomsel Flash (Indonesia) 
    

   

   May need [BlueMan]("https://wiki.ubuntu.com/BlueMan") for Bluetooth 
     Sony Ericsson K610i 
    GSM/UMTS phone via USB/Bluetooth 
    Works out-of-box 
    Smart (Philippines) 
    

   

   

    Sony Ericsson K770i 
     GPRS/UMTS phone via USB
    Works out-of-box 
    Vodafone (UK) 
    

   

   

    Sony Ericsson K810i 
     GPRS/UMTS phone via USB
    Works out-of-box 
    Bob (AT) 
    

   vendor=0fce, product=d0a1, AT+GCAP: +CGSM, +DS +COPS: 0,0,"bob",2 +CREG: 0,5 
    works with Ubuntu lucid and maverick 
     Sony Ericsson W910i 
     GPRS/UMTS/EDGE/HSDPA phone via USB
    Works out-of-box 
    Blau (E-Plus) Germany 
    

   

   

    Sony Ericsson Z770i 
     GPRS/UMTS phone via USB
    Works 
    Swisscom (Switzerland) 
    

   

   Maybe had to disable Windows driver install mode on 1st run? Don't remember exactly) 
     Motorola E770V 
    GSM/UMTS phone via USB/Bluetooth 
    Not detected by NM 
    

   [321485]("https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/321485") 
    vendor=22b8, product=3002 
    

    Nokia E52 
    GSM/UMTS phone via USB/Bluetooth  
    works with no problem on usb 
    Simobil(Vodafone), Swisscom 
    

    

   USB: Use PC Suite mode(!). Bluetooth didn't detect modem? 
  
 
**Provider info**

 Information needed to get online with certain providers. 
[IMG]file:///home/david/dlw/ubuntu/3G_files/icon_eek.png[/IMG]  If you discover you need provider information from here or elsewhere,  please file a bug against the mobile-broadband-provider-info package so  we can improve the experience for all users to a level where all  providers Just Work out of the box. [https://bugs.launchpad.net/ubuntu/+source/mobile-broadband-provider-info](https://bugs.launchpad.net/ubuntu/+source/mobile-broadband-provider-info) 
As today (16/01/09) bug #317860 at Launchpad cover a lot of Service Providers missing. ([https://bugs.edge.launchpad.net/ubuntu/+source/mobile-broadband-provider-info/+bug/317860](https://bugs.edge.launchpad.net/ubuntu/+source/mobile-broadband-provider-info/+bug/317860)) 
   **Provider** 
    **Country** 
    **APN** 
    **Dial** 
    **Username** 
    **Password** 
    **Other information** 
     3 
    Australia 
    3netaccess 
    

   N/A 
    N/A 
    

    3 
    Austria 
    drei.at 
    *99# 
    N/A 
    N/A 
    username and password can be empty 
     3 Bredband 
    Sweden 
    bredband.tre.se 
    *99# 
    dummy 
    dummy 
    APN depends on contract: 3 Bredband Kontant is  "net.tre.se", 3 Bredband is "bredband.tre.se" (the new autotool entered  "data.tre.se" which also worked, deprecated address?) UPDATE:  data.tre.se is for mobile phone usage (same speed though) and will only  give you a NATed address. May have to enter DNS servers manually (please  fix this bug): 80.251.192.244 and 80.251.192.245 
     3 Kontant 
    Sweden 
    net.tre.se 
    *99# 
    dummy 
    dummy 
    APN depends on contract. 3 Bredband Kontant is "net.tre.se", 3 Bredband is "bredband.tre.se" 
     3 
    Italy 
    naviga.tre.it 
    

   anon 
    anon 
     

    3 
    Ireland 
    3ireland.ie 
    

   3ireland 
    3ireland 
     

    3 
    UK 
    three.co.uk 
    

   three 
    three 
    APN is dependant on contract. PAYG is "three.co.uk" full contract is "3internet" 
     A1 (mobilkom) 
    Austria 
    a1.net 
    *99# 
    [EMAIL="ppp@a1plus.at"]ppp@a1plus.at[/EMAIL] 
    ppp 
    

    AT&T   
    USA  
    N/A 
    wap.cingular 
    [EMAIL="WAP@CINGULARGPRS.COM"]WAP@CINGULARGPRS.COM[/EMAIL] 
    CINGULAR1 
    username/pass just dummy data and the number needs to be *99# 
     BiBoB 
    Denmark 
    internet.bibob.dk 
    *99# 
    N/A 
    N/A 
    username and password can be empty 
     China Mobile 
    China 
    cmnet 
    

   zte 
    zte 
    

    Claro 
    Brazil 
    claro.com.br 
    *99# 
    claro 
    claro 
    Have to manually edit the DNS servers in /etc/resolv.conf, ADD nameserver 200.255.121.39  nameserver 200.169.117.14 
     Econet    
    Zimbabwe   
    econet.net 
   *99***1#/*99#  
    N/A 
    N/A 
    

    Elisa   
    Finland  
    internet 
    *99***1# 
    rlnet 
    internet 
    username "rlnet" (apparently not needed), password "internet" 
     e-moble 
    Japan 
    emb.ne.jp 
    *99***1# 
    em 
    em 
    

    Globe Visibility 
    Philippines 
    internet.globe.com.ph 
    *99# or *99***1# 
    N/A 
    N/A 
    

    Kanguru 
    Portugal 
    myconnection 
    *99***1# 
    N/A 
    N/A 
    May need dummy username and password (enter anything) DNS Servers: 62.169.67.172 and 62.169.67.171 (see [270282]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/270282") and [248630]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/248630")) 
     Kanguru (fixo) 
    Portugal 
    kangurufixo 
    *99***1# 
    N/A 
    N/A 
    Dummy username and password. DNS Servers: 62.169.67.172 and 62.169.67.171 
     ice.net 
    Sweden 
    N/A 
    #777 
    cdma 
    cdma 
    

    IM3 
    Indonesia 
    [www.indosat-m3.net]("http://www.indosat-m3.net") 
    

   im3 
    im3 
    

    Iusacell 
    México 
    N/A 
    #777 
    N/A 
    N/A 
    username/password can be anything 
     M-Budget Mobile 
    Switzerland 
    gprs.swisscom.ch 
    *99# 
    gprs 
    gprs 
    

    MCel 
    Mozambique 
    isp.mcel.mz 
    *99# 
    guest 
    guest 
     

    [MobileOne]("https://wiki.ubuntu.com/MobileOne") 
    Singapore 
    sunsurf 
    

   M1 
    M1 
    

    Movistar 
    Spain 
    movistar.es 
    

   movistar 
    movistar 
    

    MTN NG 
    Nigeria 
    web.gprs.mtnnigeria.net 
    

   web 
    web 
    Use GPRS always; username: web; password: web 
     Netcom 
    Norway 
    internet 
    

   internet 
    internet 
    

    o2 
    Germany 
    internet or surfo2 (see [FAQ]("http://o2online.custhelp.com/cgi-bin/o2online.cfg/php/enduser/std_adp.php?p_sid=X5JmnObj&p_accessibility=0&p_redirect=&p_lva=478&p_li=&p_faqid=472&p_created=1182170843")) 
    

   N/A 
    N/A 
    any username and password 
     o2 
    Ireland 
    open.internet 
    

   gprs 
    gprs 
     

    Optimus 
    Portugal 
    myconnection 
    *99***1# 
    N/A 
    N/A 
    May need dummy username and password (enter anything) 
     o2 
    UK 
    mobile.o2.co.uk 
    *99# 
    N/A 
    N/A 
    

    o2 PAYG 
    UK 
    m-bb.o2.co.uk 
    *99# 
    o2bb 
    password 
    Username & password may be anything 
     Optus Prepaid 
    Australia 
    preconnect 
    

   N/A 
    N/A 
    Needs to be able to recieve SMS's to activate  the SIM. Windows utility has this capability. Works perfectly in Ubuntu  when activated. 
     Orange (formerly ONE) 
    Austria 
    orange.web or fullspeed or web.one.at 
    *99# 
    web 
    web 
    

    Orange 
    UK 
    orangeinternet or internetvpn (see [FAQ]("http://www.business.orange.co.uk/servlet/Satellite?pagename=Business&c=OUKPage&cid=1044134122137"))
     

   orange 
    orange 
    

    Play 
    Poland 
    internet 
    *99# 
    N/A 
    N/A 
    Leave user and password blank 
     Powertel 
    Zimbabwe 
    

   #777 
    111 
    111 
    

    PT. SATelindo C 
    Indonesia 
    indosat3g 
    

   indosat 
    indosat 
    

    Pro XL 
    Indonesia 
    [www.xlgprs.net]("http://www.xlgprs.net") 
    

   xlgprs 
    proxl 
    

    Proximus 
    Belgium 
    internet.proximus.be 
    *99# 
    test 
    test 
    May need "Prefer GPRS". Used Huawei e220 
     Reliance [NetConnect]("https://wiki.ubuntu.com/NetConnect") Broadband+ 
    India 
   N/A 
   #777
    Your_mobile_number 
   Your_mobile_number
    [NetworkMangaer]("https://wiki.ubuntu.com/NetworkMangaer") should ask Username / Password before completing wizards 
     Safaricom 
    Kenya 
    web.safaricom.com 
    *99# 
    web 
    web 
    

    SFR 
    France 
    websfr 
    

   websfr 
    websfr 
    

    Smart 
    Philippines 
    Internet or SmartBro 
    *99# 
    N/A 
    N/A 
    The PPP Authentication Method should be set to PAP. DNS Address preferably configured to OpenDNS or Google since ISPs' DNS not reliable 
     Sprint 
    USA 
    unknown 
    #777 
    N/A 
    N/A 
    number: #777 authenticates via ESN 
     Simyo    
    Spain   
    gprs-service.com 
    

   N/A 
    N/A 
    

    Sunrise 
    Switzerland 
    internet 
    *99# 
     

    

   

    Swisscom 
    Switzerland 
    gprs.swisscom.ch 
    *99# 
    gprs 
    gprs 
    

    T-Mobile 
    Czech Republic 
    internet.t-mobile.cz 
    *99# 
    gprs 
    gprs 
    

    T-Mobile    
    USA   
    internet2.voicestream.com  
    

   N/A 
    N/A 
    

    Tata Indicom Photon+ 
    India 
    N/A 
    #777 
    internet 
    internet 
    

    Tele 2   
    Sweden 
    mobileinternet.tele2.se 
    *99# 
    

   

   May need dummy username and password (enter anything) 
     Telkomsel Flash - Time based 
    Indonesia 
    flash 
    

   flash 
    flash
    

    Telkomsel Flash - Unlimited 
    Indonesia 
    internet 
    *99# 
    

   

   

    [TeliaSonera]("https://wiki.ubuntu.com/TeliaSonera") 
    Sweden 
    online.telia.se 
    

   3G 
    internet 
    

    Telstra 
    Australia 
    Telstra.WAP or Telstra.Internet 
    *99# 
    N/A 
    N/A 
    

    Telenor 
    Serbia 
    internet 
    *99# 
    telenor 
    gprs 
    

    Telenor 
    Sweden 
    services.telenor.se 
    

   

   

   

    Tigo 
    Colombia 
    web.colombiamovil.com.co 
    *99# 
    N/A 
    N/A 
     

    TIM 
    Italy 
    ibox.tim.it 
    

   anon 
    anon 
    

    TMN 
    Portugal 
    internet 
    *99# 
    

   

   username and password can be empty 
     TW Mobile 
    Taiwan 
    internet 
    *99# 
    

   

   username/password can be anything 
     Verizon 
    USA 
    N/A 
    #777 
    <phonenum>@vzw3g.com 
    vzw 
    username/pass can be blank 
     Vodacom 
    South Africa 
    internet 
    

   vodafone 
    vodafone 
    

    Vodafone 
    Germany 
    web.vodafone.de 
    

   vodafone 
    vodafone 
    

    Vodafone 
    Hungary 
    standardnet.vodafone.net 
   *99***1# 
    ANY 
    ANY
    Normal graphics 
     Vodafone 
    Hungary 
    internet.vodafone.net 
   *99***1# 
    ANY 
    ANY
    Reduced graphics 
     Vodafone 
    Hungary / Prepaid 
    vitamax.snet.vodafone.net 
   *99***1# 
    ANY 
    ANY
    Normal graphics 
     Vodafone 
    Hungary / Prepaid 
    vitamax.internet.vodafone.net 
   *99***1# 
    ANY 
    ANY
    Reduced graphics 
     Vodafone 
    Italy 
    web.omnitel.it 
    

   vodafone 
    vodafone 
    

    Vodafone 
    Ireland 
    hs.vodafone.ie 
    

   vodafone 
    vodafone 
    

    Vodafone 
    Netherlands 
    live.vodafone.com 
    

   vodafone 
    vodafone 
    

    Vodafone 
    Portugal 
    internet.vodafone.pt 
    

   vodafone 
    vodafone 
    

    Vodafone 
    Romania 
   internet.vodafone.ro 
    

   internet.vodafone.ro 
    vodafone 
    

    Vodafone 
    Spain 
    ac.vodafone.es 
    

   vodafone 
    vodafone
    

    Vodafone 
    UK 
    internet 
    

   vodafone 
    vodafone 
    

    VIP 
    Croatia 
    data.vip.hr 
    

   38591 
    38591 
    

    Virgin Mobile 
    Australia 
    virgininternet 
    

   N/A 
    N/A 
    

    Virgin Mobile Prepaid
    Australia 
    VirginBroadband 
    

   N/A 
    N/A 
    Need to disable CHAP (via Network Manager, edit settings, PPP settings tab) 
     Wana 
    Morocco 
    

   #777 
    wana 
    wana 
    

    Welho 
    Finland 
    internet.welho.fi 
   *99# 
   N/A
    N/A 
    In Network-manager chose DNA and modify APN 
     Wind 
    Canada 
    internet.windmobile.ca 
    *99# 
    

   

   

    Wind 
    Italy 
    internet.wind 
    

   anon 
    anon 
    

    XS4ALL 
    Netherlands 
    umts.xs4all.nl 
    (umts/gprs default) 
    chosen username 
    chosen password 
    Username and password are chosen when you register for the service. 
     Yesss 
    Austria 
    web.yesss.at 
    *99# 
    dummy 
    dummy 
    

    Yoigo    
    Spain   
    internet 
    *99***1# 
    yoigo 
    yoigo 
    

 

   
                          NetworkManager/Hardware/3G  (last edited 2011-10-02 15:03:51 by [guptaeshant]("https://launchpad.net/%7Eguptaeshant"))
            
      
                
          
                
  
                               The material on this wiki is available under a free license, see      [Copyright / License]("https://help.ubuntu.com/community/License") for details.

---

