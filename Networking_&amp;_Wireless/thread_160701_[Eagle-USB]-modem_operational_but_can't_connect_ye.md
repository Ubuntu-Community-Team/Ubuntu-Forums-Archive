---
title: "[Eagle-USB]-modem operational but can't connect yet"
date: 2006-04-15
forum: Networking &amp; Wireless
---

### Post by ThE_nEtTeR on 2006-04-15
Hi!

i think i've sucesfully installed eagle-usb after reading a lot, when i configured with eagleconfig my connection, eveything went fine. later i typed sudo startadsl but when i try to browse a webpage,i get an error, it says it couldn't find the URL.

this is the exit of eaglestat:

casa@teruel:~$ eaglestat
eagle-usb status display
-------------------------------------------------------------
Driver version 2.3.2 Chipset: Eagle0
Vendor ID : 0x1110 Product ID : 0x9021 Rev: 0x500b
USB Bus : 001 USB Device : 003 Dbg mask: 0x0
Ethernet Interface : eth0
MAC: 00:60:4c:36:96:c7
Tx Rate 320 Rx Rate 1024
FEC 0 Margin 41 Atten 18 dB
VID-CPE 34 VID-CO 28 HEC 0
VPI 8 VCI 35 Delin GOOD
Cells Tx 41 Cells Rx 0
Pkts Tx 36 Pkts Rx 0
OAM 0 Bad VPI 0 Bad CRC 0
Oversiz. 0

Modem is operational

i also enabled in system/network the eth0 interface and editted /etc/resolv.conf with some DNS i found for my provider (Wanadoo,Spain) but i'm starting to doubt if they are correct.

Hope you can help me, thanks!!!

---

