---
title: "Ubuntu 11.10 Network Manager Problem"
date: 2011-11-21
forum: Networking &amp; Wireless
---

### Post by shrek1 on 2011-11-21
hey , can any one help me? i am using ubuntu 11.10 with WiFi connection. My network manager hangs , means while i work on my laptop my internet connection disconnects automatically but network panel on top right corner still shows that i am connected & when i try to open network settings nothing happens it not opens. But my other applications still work properly. But when i tries to reboot my system it hangs while it rebooting so i have to shutdown it forcely by power off button .Why it happens i don't know

---

### Post by hutchy on 2011-11-22
I am getting the same problem.  I'm using a HP G72 laptop.  Here are the specs from HardInfo:


-PCI Devices-
Host bridge		: Intel Corporation Core Processor DRAM Controller (rev 02)
VGA compatible controller		: Intel Corporation Core Processor Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
Communication controller		: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
USB Controller		: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20 [EHCI])
Audio device		: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
PCI bridge		: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05) (prog-if 00 [Normal decode])
PCI bridge		: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05) (prog-if 00 [Normal decode])
USB Controller		: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20 [EHCI])
PCI bridge		: Intel Corporation 82801 Mobile PCI Bridge (rev a5) (prog-if 01 [Subtractive decode])
ISA bridge		: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
SATA controller		: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05) (prog-if 01 [AHCI 1.0])
SMBus		: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
Ethernet controller		: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
**Network controller		: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe**
Host bridge		: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
Host bridge		: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
Host bridge		: Intel Corporation Core Processor QPI Link 0 (rev 02)
Host bridge		: Intel Corporation Core Processor QPI Physical 0 (rev 02)
Host bridge		: Intel Corporation Core Processor Reserved (rev 02)
Host bridge		: Intel Corporation Core Processor Reserved (rev 02)

---

### Post by hutchy on 2011-11-22
I think I've fixed it.  

Setting the MTU to 1500 rather than Auto seems to have made the connection stable.
[http://mylinuxramblings.wordpress.com/2011/10/16/how-to-stop-ubuntu-11-10-wireless-dropping-out/](http://mylinuxramblings.wordpress.com/2011/10/16/how-to-stop-ubuntu-11-10-wireless-dropping-out/)

---

