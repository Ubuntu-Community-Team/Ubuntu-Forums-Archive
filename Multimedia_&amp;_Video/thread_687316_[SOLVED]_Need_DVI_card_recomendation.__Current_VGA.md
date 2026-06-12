---
title: "[SOLVED] Need DVI card recomendation.  Current VGA unsatisfactory."
date: 2008-02-04
forum: Multimedia &amp; Video
---

### Post by PhilOSparta on 2008-02-04
I purchased a nice 22 inch LCD monitor that doesn't perform very well with my current ATI Radeon Xpress 200G graphics card.  ( It is VGA only! )

The problem is two fold: 
 1.) The low levels of grey on the gamma1024 test pattern are white.  
 2.) At recommended screen resolution, the left side of the screen has a 4 inch black bar.

Tests already performed:
1. Switched monitor to another PC with a DVI port.   It performed beautifully.
2. Performed the usual ***sudo dpkg-reconfig xserver-xorg*** routines.  The graphics board and monitor were detected, and the proper driver was installed.
3. Non of the monitor's OSD controls have much effect on the problems.

Can anyone recommend a graphics card whose manufacturer supports Linux?
This PC is used for photographic work, so I'm looking for a modest cost.

Thanks.

Phil

---

### Post by swazidoughman on 2008-02-04
Well if you where to get a new GFX card for linux,  then you should get an Nvidia card, because they have the best linux support. another thing you should have mentioned is your budget, but you can get a Geforce 8400GS for under $100 or if you want to treat yourself then get a Geforce 8800GT for as low of a price as 210 (256mb version).   :popcorn:

---

### Post by PhilOSparta on 2008-02-04
> **swazidoughman said:**
> Well if you where to get a new GFX card for linux,  then you should get an Nvidia card, because they have the best linux support. another thing you should have mentioned is your budget, but you can get a Geforce 8400GS for under $100 or if you want to treat yourself then get a Geforce 8800GT for as low of a price as 210 (256mb version).   :popcorn:

Thanks.  I believe it's important to support Mfg.s that support Linux.
Just purchased the Dell Inspiron 530N preloaded with Ubuntu.
Budget wise, the lower the better as long as it works.  The fastest game we play is solitare.:)

---

### Post by swazidoughman on 2008-02-04
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814121086](http://www.newegg.com/Product/Product.aspx?Item=N82E16814121086)


This is actually cheaper than i thought, only 50 bucks & should provide a better image quality & performance than your integrated VGA.

check to make sure that you have PCI-Express

---

### Post by PhilOSparta on 2008-02-04
> **swazidoughman said:**
> 
check to make sure that you have PCI-Express

This is the output from  lspci  
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS480 [Radeon Xpress 200G Series]
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:05.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
02:09.0 Modem: Motorola SM56 Data Fax Modem (rev 04)

I guess I need a regular PCI.

---

### Post by swazidoughman on 2008-02-06
> **PhilOSparta said:**
> This is the output from  lspci  
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS480 [Radeon Xpress 200G Series]
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:05.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
02:09.0 Modem: Motorola SM56 Data Fax Modem (rev 04)

I guess I need a regular PCI.


well if i do recall correctly i think PCI-E on an Xpress200 chip set may be what all Xpress200 chipsets have, but im not sure about that, but for basic video (like you are doing) i guess that any PCI card should be a okay. but YOU SHOULD GET AN NVIDIA based gfx card. ATI has generally terrible linux suppor. :)

---

