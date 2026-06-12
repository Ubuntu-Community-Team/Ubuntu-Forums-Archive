---
title: "multimedia Video"
date: 2008-12-02
forum: Multimedia Software
---

### Post by SJ_tu on 2008-12-02
Hi! I am new to linux (Ubuntu 8.10). I was trying to capture DV through firewire from Sony DCR-TRV350 using kino. But it shows the following message:raw1394 kernel module not loaded or failire to read/write/dev/raw1394!

here is some info from my laptop

sri@sri-laptop:~$ lsmod | grep 1394
video1394              23868  0 
dv1394                 25180  0 
raw1394                32348  0 
ohci1394               37936  2 video1394,dv1394
ieee1394               96324  5 video1394,dv1394,raw1394,sbp2,ohci1394
sri@sri-laptop:~$ sudo lshw | grep 1394
[sudo] password for sri: 
             description: FireWire (IEEE 1394)
             configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=3 module=ohci1394
sri@sri-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01)
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:09.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:0a.0 CardBus bridge: Texas Instruments PCI4410 PC card Cardbus Controller (rev 02)
00:0a.1 FireWire (IEEE 1394): Texas Instruments PCI4410 FireWire Controller (rev 02)
00:0c.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
00:0d.0 USB Controller: NEC Corporation USB (rev 43)
00:0d.1 USB Controller: NEC Corporation USB (rev 43)
00:0d.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
00:0e.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1

I badly need your help, I have very little knowledge about linux
Thanks in advance

---

### Post by SJ_tu on 2008-12-09
is there anybody out there?:lolflag:

---

### Post by DuncanNZ on 2009-02-23
Hi there, since you're having trouble with capture over Firewire to Kino you might want to look at my recent update of the [https://help.ubuntu.com/community/Firewire](https://help.ubuntu.com/community/Firewire) page. Please let me know if there are any problems with that guide.

---

### Post by roberto.eiberle on 2009-02-23
run sudo kino in terminal

---

