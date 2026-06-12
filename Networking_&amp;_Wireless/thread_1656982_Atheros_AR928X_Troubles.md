---
title: "Atheros AR928X Troubles"
date: 2010-12-31
forum: Networking &amp; Wireless
---

### Post by Raptor354 on 2010-12-31
I recently put Ubuntu 10.10 64-bit on my laptop, which has an Atheros AR928X wireless card.  Unfortunately, I can't even enable the card.  Yes, the hardware network switch is on.

It works flawlessly in Windows, which I'm dual-booting from.

Note that my Marvell LAN card works nicely.

Relevant parts of program outputs are below.

iwconfig
```
wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
```

dmesg | grep wlan0
```
[  142.859176] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

dmesg | grep Atheros
```
[   17.395667] phy0: Atheros AR9280 MAC/BB Rev:2 AR5133 RF Rev:d0: mem=0xffffc900050e0000, irq=17
```

lshw -C Network
```
  *-network DISABLED      
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 01
       serial: 70:1a:04:03:3d:78
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:f69f0000-f69fffff
```

Any thoughts?

Raptor354

---

### Post by Raptor354 on 2010-12-31
Ok, so I seem to have fixed it.

Just so everybody knows, I followed [drpjkurian's directions]("http://ubuntuforums.org/showthread.php?t=1484242") for installing Madwifi, and it works well now.

Mission acomplished :KS

---

