---
title: "Recent wireless slowdown"
date: 2010-10-20
forum: Networking &amp; Wireless
---

### Post by Rundi on 2010-10-20
I am using Ubuntu 10.04 LTS with a wireless card. Recently (I think it was within the last week) my internet connection degraded noticeably. I would describe it as dragging and lurching as it loads pages. At first I attributed this to internet problems, but when it persisted I began to do some checking. There is no similar problem with the windows computers in the house (the one sitting right next to my Linux box, in fact). Since I have been using Ubuntu 10.04 for some time and had no problems, and since the signal strength has not changed, I'm guessing some upgrade that the upgrade manager installed is the cause of this sudden problem cropping up. But I am at a loss as to what caused this, or how to fix it.

The relevant portion of dmesg:

[   11.319936] ndiswrapper: driver lsipnds (Cisco-Linksys, LLC.,08/15/2003,3.07.08.2003) loaded
[   11.320250]   alloc irq_desc for 17 on node -1
[   11.320254]   alloc kstat_irqs on node -1
[   11.320263] ndiswrapper 0000:02:02.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.436384] ndiswrapper: using IRQ 17
[   11.893061] wlan0: ethernet device 00:0f:66:3d:e6:d1 using NDIS driver: lsipnds, version: 0x30007, NDIS version: 0x501, vendor: 'Wireless-B PCI Adapter', 17FE:2120.5.conf
[   11.893080] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
[   11.901899] usbcore: registered new interface driver ndiswrapper


Any help would be much appreciated.

---

### Post by Rundi on 2010-10-21
Today I downloaded the most recent updates which the Update Manager notified me of, and that fixed my problem. I guess somebody realized there was a flaw in an earlier update.

I'm glad it was fixed, and I didn't have to do anything.

---

