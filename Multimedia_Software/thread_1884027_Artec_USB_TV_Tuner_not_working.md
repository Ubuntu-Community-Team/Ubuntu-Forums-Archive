---
title: "Artec USB TV Tuner not working"
date: 2011-11-20
forum: Multimedia Software
---

### Post by Super Nade on 2011-11-20
Hi,

Can somebody kindly help me setup my TV Tuner stick?

Make and Model: Artec TV18R USB TV Tuner
OS: Ubuntu 11.10 64bit
Hardware: MSI MS1656-US (GX640 barebones): i5 580M, 2xIntel X25M SSDs, Radeon HD5850M,Realtek sound.

Logs and messages:
```
antillar@antillar-MS-1656:/usr/share/dvb/atsc$ **[COLOR=Red]sudo lsusb[/COLOR]**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 003: ID ffc0:001f  
Bus 002 Device 005: ID 05d8:8117 Ultima Electronics Corp. 
``````
antillar@antillar-MS-1656:/usr/share/dvb/atsc$ [COLOR=Red]**sudo lspci**[/COLOR]
[sudo] password for antillar: 
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Broadway PRO [Mobility Radeon HD 5800 Series]
01:00.1 Audio device: ATI Technologies Inc Juniper HDMI Audio [Radeon HD 5700 Series]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
04:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
04:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
04:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
04:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
04:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
05:00.0 Network controller: Intel Corporation Ultimate N WiFi Link 5300
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
antillar@antillar-MS-1656:/usr/share/dvb/atsc$ 

```I've attached the output of lshw to this post. So, it seems that the tuner is being detected, but the light on it does not turn on? Not sure what is going on.

Thank you!

---

### Post by Super Nade on 2011-11-22
Anybody?

---

### Post by wolfen69 on 2011-11-22
[http://nthrbldyblg.blogspot.com/2009/07/artec-dvb-usb-in-linux.html](http://nthrbldyblg.blogspot.com/2009/07/artec-dvb-usb-in-linux.html)

---

