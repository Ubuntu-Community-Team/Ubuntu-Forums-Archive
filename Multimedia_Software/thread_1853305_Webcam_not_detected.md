---
title: "Webcam not detected"
date: 2011-10-02
forum: Multimedia Software
---

### Post by dr_anirudh_shukla on 2011-10-02
Am unable to use my inbuilt laptop webcam. I installed cheese. Cheese does not detect it. 
My version is -->
Linux anirudh-VGN-CR36G-B 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:18:14 UTC 2011 i686 i686 i386 GNU/Linux
{Ubuntu 11.04 Natty Narwhal}
Laptop model no. -  (Sony VAIO CR36G/B) 
Please help.
Thanks a zillion.

---

### Post by papibe on 2011-10-02
Could you post the result of these commands?
```
$ lsusb

$ lspci
```
Please paste your results using code tags (the # icon you see while editing your post).

Regards.

---

### Post by dr_anirudh_shukla on 2011-10-02
Hi Papibe,

Thanks for the prompt reply.

lsusb -->>

Bus 007 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 1bcf:0007 Sunplus Innovation Technology Inc. Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 044e:3012 Alps Electric Co., Ltd 
Bus 003 Device 004: ID 044e:3013 Alps Electric Co., Ltd 
Bus 003 Device 003: ID 044e:3010 Alps Electric Co., Ltd Bluetooth Adapter
Bus 003 Device 002: ID 044e:3011 Alps Electric Co., Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0bc2:3008 Seagate RSS LLC 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 05ca:1839 Ricoh Co., Ltd Visual Communication Camera VGP-VCC6 [R5U870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

lspci -->>

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon X2300
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
08:07.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:07.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:07.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

Thanks.

---

### Post by papibe on 2011-10-02
> **dr_anirudh_shukla said:**
> 
Bus 001 Device 003: ID 05ca:1839 Ricoh Co., Ltd Visual Communication Camera VGP-VCC6 [R5U870]
There it is a Ricoh webcam ID **05ca:1839**.

According to [this]("http://www.qbik.ch/usb/devices/search_res.php?pattern=ricoh"), the default Lunix drivers won't support it (at least the exact model). However, I found these 2 thread with a third party driver that solved their problem: [this]("http://ubuntuforums.org/showthread.php?t=1321338") one, and this [other]("http://ubuntuforums.org/showthread.php?t=821343") one.

Note that this is just to point you in the direction of a possible solution. I haven't tested those solutions. Also now that you know details about your wecam, may be you can search and find other solutions.

I hope it helps,
Regards.

---

### Post by sanderj on 2011-10-02
I guess this is your camera:


```
Bus 001 Device 003: ID 05ca:1839 Ricoh Co., Ltd Visual Communication Camera VGP-VCC6 [R5U870]

```

Googling for 05ca:1839 leads to the ppa mentioned here: [http://ubuntuforums.org/showpost.php?p=5705645&postcount=13](http://ubuntuforums.org/showpost.php?p=5705645&postcount=13)

Can you try that?

---

### Post by dr_anirudh_shukla on 2011-10-02
Thanks a zillion. It worked. I followed the links and then followed the instructions and now its working just fine. Thanks again.

---

