---
title: "Can't connect to the internet Wired or Wireles"
date: 2009-01-10
forum: Networking &amp; Wireless
---

### Post by football_dynasties on 2009-01-10
I just bought a new HP laptop and can't get it to connect to the internet. I've found instructions on how to get my wireless card working, but I can't even get that far. I've plugged my ethernet cable into it and screwed around with the settings, but I'm still not having any luck. Help please!

---

### Post by 2hot6ft2 on 2009-01-10
Which one of the thousands of HP laptops? Specs? Which version of ubuntu # 32 bit 64 bit? Info, info, info? My crystal ball is in the shop...:(

---

### Post by football_dynasties on 2009-01-10
Sorry, It's Ubuntu 8.10 and this is the laptop [http://www.bestbuy.com/site/olspage.jsp?skuId=9166635&type=product&id=1218041148373#tabbed-customerreviews](http://www.bestbuy.com/site/olspage.jsp?skuId=9166635&type=product&id=1218041148373#tabbed-customerreviews)

---

### Post by 2hot6ft2 on 2009-01-10
What do you get with ```
lspci
``` in a terminal?
Applications>Accessories>Terminal

---

### Post by football_dynasties on 2009-01-11
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Hewlett-Packard Company Unknown device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
08:00.0 System peripheral: JMicron Technologies, Inc. Unknown device 2382
08:00.2 SD Host controller: JMicron Technologies, Inc. Unknown device 2381
08:00.3 System peripheral: JMicron Technologies, Inc. Unknown device 2383
08:00.4 System peripheral: JMicron Technologies, Inc. Unknown device 2384
09:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)

---

### Post by 2hot6ft2 on 2009-01-11
> **football_dynasties said:**
> 
09:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
This is your wifi card and chip info, so you probably have the AR5007 minipci card and it uses the AR242x chipset

For wifi you'll find a lot of people with that same chipset that got it working with a little searching. At least now you know what to search for.

Here are some that have that working.
[http://ubuntuforums.org/showthread.php?t=1035944&highlight=AR242x](http://ubuntuforums.org/showthread.php?t=1035944&highlight=AR242x)
[http://ubuntuforums.org/showthread.php?t=1031023&highlight=AR242x](http://ubuntuforums.org/showthread.php?t=1031023&highlight=AR242x)
another one
[http://ubuntuforums.org/showthread.php?t=1032960&highlight=AR242x](http://ubuntuforums.org/showthread.php?t=1032960&highlight=AR242x)

> **football_dynasties said:**
> 
0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)
This is the info for your Ethernet card.

It should just work if you plug it in while it's off and boot it up with it already connected for wired.
If not do a search here in the forums for RTL8101E

---

### Post by 2hot6ft2 on 2009-01-11
By the way if you used the button switch to turn the wifi off in windows you need to turn it back on in windows since the button switch doesn't work in ubuntu.

Sorry I couldn't be of more help but got to go.

---

### Post by football_dynasties on 2009-01-11
It's still not working. I've tried hooking up to both the router and directly to the modem and I'm not getting anything. 

Edit: I just tried it in Vista and it connects no problem. Any ideas?

Edit: Nevermind, I restarted for the fourth time and it works now.

---

