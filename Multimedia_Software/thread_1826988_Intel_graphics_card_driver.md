---
title: "Intel graphics card driver"
date: 2011-08-17
forum: Multimedia Software
---

### Post by fluizp on 2011-08-17
Hello!

I installed Ubuntu 11.04 in a laptop that I bought a few weeks ago. Well, I am always using a projector through the VGA port, and the Ubuntu graphics driver (automatically installed) makes both laptop monitor and projector stay with same resolution. For the projected surface it is ok, but since the resolution is decreased, in the laptop monitor appears two black stripes (one in the left and one in the right). This way, I need to install a better driver for the graphics card

The only information regarding the graphics card is its name: Mobile Intel HD Graphics, without any numeric reference. I've searched at Intel website, but I didn't find any driver for it.

Well, I don't want to be surprised being without access to X after installing the wrong driver. After executing the lspci commando, this is the result:

fabyo@Guapeca:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
06:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
15:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 20)
15:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 20)
15:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 20)
15:00.4 System peripheral: JMicron Technology Corp. xD Host Controller (rev 20)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)

So, I must install the "Intel Corporation Core Processor Integrated Graphics Controller" driver.

I've searched without success. Any tipp from where can I find this driver?

---

