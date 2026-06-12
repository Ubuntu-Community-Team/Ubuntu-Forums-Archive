---
title: "Crunchbang - Wireless Stops Randomly"
date: 2009-12-29
forum: Networking &amp; Wireless
---

### Post by s.fox on 2009-12-29
Hello,

I am experiencing a very odd problem with #!crunchbang linux 9.04 (Ubuntu based OS).  

The wireless on my Sony Vaio suddenly stops working after a period of upto 2 hours.  The network connection icon still shows that it is still connected and has 85-100% connectivity.  Other wireless devices are able to access the internet fine.

The only solution that seems to work is to reboot the laptop.  This is not ideal and I seek the assistance to help with a permanent solution.

Output from lspci:

```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4380 (rev 10)
02:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
0b:03.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
0b:03.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0b:03.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
```Output from dmesg | tail :

```
dmesg | tail
[   46.740836] wlan0: RX AssocResp from ffff8801320a4016 (capab=0xc31 status=0 aid=1)
[   46.740839] wlan0: associated
[   46.744924] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   46.835650] cfg80211: Calling CRDA for country: GB
[   46.837697] cfg80211: Current regulatory domain updated by AP to: GB
[   46.837701]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   46.837703]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   57.712054] wlan0: no IPv6 routers present
[   80.850312] iwlagn 0000:02:00.0: iwl_tx_agg_start on ra = ffff880133daa740 tid = 0
[   80.850363] iwlagn 0000:02:00.0: HW queue is empty

```Not sure how useful the dmesg is going to be as the wifi is currently working.

Any help greatly appreciated.  If any more information is needed please do ask. Many thanks

-Silver Fox

---

### Post by s.fox on 2009-12-30
Hello,

After a bit of research and a very helpful chat on IRC I have been able to resolve the issue.  I replaced the network manager with wicd.  This seems to have fixed it.

-Silver Fox

---

### Post by Roasted on 2009-12-30
How's WICD been for you? It would consistently drop my wifi connection every 5 minutes or so, whereas NetworkManager would not. I liked WICD a lot though. It's interface and features were really nice. But I gotta use what works. :(

---

### Post by s.fox on 2009-12-31
Hello,

Its been very reliable with no connection issues whatsoever.  From what I understand its less resource demanding too, so I might start using wicd on all future installs.

I do agree that you have got to use what works sometimes :)

-Silver Fox

---

### Post by Roasted on 2009-12-31
Fortunately something like WICD exists, because it seems either 1 or the other works. Ahh, the power of choice. :)

---

