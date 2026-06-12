---
title: "Madwifi-ng"
date: 2009-10-28
forum: Networking &amp; Wireless
---

### Post by mearturo on 2009-10-28
Dear all, 

I just installed MADWIFI in my ubuntu ws (2.6.28-16-generic 64bits), but I can't see the device (ath0 or wifi0).

The compilation was successful, the "hardware drivers" sees the driver, lsmod |grep ath shows this:
ath_pci               220608  0 
wlan                  255008  1 ath_pci
ath_hal               399584  1 ath_pci

lspci -v:
04:00.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
    Subsystem: Netgear Device 5b00
    Flags: medium devsel, IRQ 19
    Memory at 124000000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: [44] Power Management version 2
    Kernel modules: ath_pci, ath5k

As usual, any pointer or help will be greatly appreciated.

Kind regards

---

