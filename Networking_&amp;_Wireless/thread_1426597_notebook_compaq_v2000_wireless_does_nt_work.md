---
title: "notebook compaq v2000 wireless does nt work"
date: 2010-03-10
forum: Networking &amp; Wireless
---

### Post by gabak on 2010-03-10
hi i have been reading several forums most of them very old one like 2006 and i tried them and neither of them have work.

[http://ubuntuforums.org/showthread.php?t=190177&highlight=wireless](http://ubuntuforums.org/showthread.php?t=190177&highlight=wireless)

i have a notebook compaq v2000 and everything works except wifi.
the wifi light is off and even when i press the buttom it does nt work.


this is the hardware i have
lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller

---

### Post by theSshow on 2011-01-10
Any new findings in this area? I am also having the same problems with this notebook.

---

### Post by PatchesTheCaveman on 2011-01-10
To install the Broadcom driver go to System > Administration > Additional Drivers (or Hardware Drivers on versions older than 10.10).  Select the *Broadcom STA wireless driver* and click Install.  You will need a working wired Ethernet Internet connection to download and install the driver.

---

### Post by chah on 2011-01-10
Broadcom drivers for Linux are a little bit under-supported. I quote you from "Hacking Wireless Exposed", by Johnny Cache and Vincent Liu, the 2007 Edition, p102-103:
"Broadcom was one of the first vendors to market with an 802.11g chipset, allowing them to gain quite a foothold in the market. This is unfortunate, because these chipsets are totally proprietary and Broadcom easily deserves the "least useful to open-source driver developers" title. The most likely Broadcom chip you will run across is the popular bcm4318. If you have a new laptop and it doesn't have a Centrino (aka Intel pro wireless) chip inside, odds are it's a Broadcom chip... snip ...

A native Linux driver for these chips does exist (bcm43xx), but it's very hard to get it working. The driver seems to be under heavy development and maturing, but it is unlikely that even then this chipset will be much use to anyone interested in wireless security. Don't buy a card with a Broadcom chipset. Even if your laptop has one built in, buy a different card".

For your info, these authors recommend cards with Atheros and Ralink chipsets as both have decent open-source support. 

Another note is this information was published in 2007. Perhaps by now things have changed. But don't be too surprised if the chipset in your compaq (which according to lspci is the bcm4318 ) isn't supported under Linux. An alternative is to use a windows driver wrapped in ndiswrapper. Sorry, I don't know much about that.

---

### Post by chah on 2011-01-10
There's some hope. See this page
[http://wireless.kernel.org/en/users/Drivers/b43]("http://wireless.kernel.org/en/users/Drivers/b43")

---

### Post by theSshow on 2011-01-18
Ah thanks for all the info.  I tried everything above, and nothing seems to work.  

Right now, I have the Broadcom B43 wireless driver instaled under "Additional Drivers," but it does not work. The wireless icon appears on the tool bar, but when I click "Enable Wireless" it can't detect anything.

---

