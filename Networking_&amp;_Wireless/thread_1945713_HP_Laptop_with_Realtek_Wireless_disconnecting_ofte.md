---
title: "HP Laptop with Realtek Wireless disconnecting often or not connecting at all"
date: 2012-03-23
forum: Networking &amp; Wireless
---

### Post by Poisoned on 2012-03-23
I have an HP Dv6 6c15nr laptop running xubuntu and the wireless randomly  disconnects or wont connect to the internet at all. I have made sure  the power management is off, the driver for my specific card is  installed (properly) but still no luck. if i put my card in monitor mode  where it lists the interface, the chipset, and the drivers it lists the  chipset as <unknown> . 

If i run sudo lspci -v the response i get is 

> 
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
    Subsystem: Hewlett-Packard Company Device 1658
    Flags: bus master, fast devsel, latency 0, IRQ 41
    I/O ports at 4000 [size=256]
    Memory at c0404000 (64-bit, prefetchable) [size=4K]
    Memory at c0400000 (64-bit, prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
    Capabilities: [d0] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number ec-04-00-00-68-4c-e0-00
    Kernel driver in use: r8169
    Kernel modules: r8169

07:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
    Subsystem: Hewlett-Packard Company Device 1629
    Flags: bus master, fast devsel, latency 0, IRQ 17
    I/O ports at 3000 [size=256]
    Memory at c4500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 01-91-81-fe-ff-4c-e0-00
    Kernel driver in use: rtl8192ce
    Kernel modules: r8192ce_pci, rtl8192ce

iwconfig returns (on the rare occasion that it stays connected)

> 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"CCSU_OPEN"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:22:55:58:9F:D1   
          Bit Rate=5.5 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

the driver installed in Additional Hardware Drivers displays as Linux Driver for Realtek RTL819x WiFi Cards

Also i cannot connect to a p-link router of mine that has mac address filtering enabled on it, even  though the address of all of my interfaces are entered into the filter  correctly.


Any help?

---

### Post by praseodym on 2012-03-23
Which encryption mode do you use? I recommend pure WPA2-AES.

---

### Post by ccrs8 on 2012-03-29
The wireless disconnecting issue seems to be the exact same as what is experienced in this thread:
[http://ubuntuforums.org/showthread.php?t=1916776](http://ubuntuforums.org/showthread.php?t=1916776)

Looks like that particular wireless card is just terrible.  I personally experienced the problem (as you can see in my replies in that thread) and ended up getting an inexpensive Intel wireless card instead (the suggestion in that thread).  At this very moment I'm using my laptop with my new Intel card on the exact type of wireless network that I previously would have had problems with and have yet to drop my connection.

---

