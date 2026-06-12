---
title: "Broadcom 4312 Low-power card no longer works"
date: 2011-02-21
forum: Networking &amp; Wireless
---

### Post by RobotGymnast on 2011-02-21
I set up Ubuntu using Wubi on my 64-bit Dell computer with a WLAN 1395 Minicard (Broadcom 4312 low-power wireless firmware).

The network appears to work sporadically on both my Windows 7 and Ubuntu boots, and cuts out for no reason. The Windows 7 boot claims not to see the network (it's hidden SSID), and the Ubuntu boot can see it, but refuses to connect, prompting for a re-entry of the password. Occasionally, it works under both, for seemingly no reason.

Reinstalling the Windows wireless drivers causes my wireless to work perfectly, but reinstalling Ubuntu wireless firmware and drivers causes both boots to fail network connection.

Any help?

---

### Post by thefasterblueone on 2011-02-21
While plugged into the Ethernet cable let Ubuntu get all the updates.

Then check  System> Administration> Additional Drivers for any proprietary drivers it may need.

Then post the output of this in your next post.

```
sudo lshw -C network
```

---

### Post by RobotGymnast on 2011-02-22
All my updates are installed, as is the B43 firmware (not the STA firmware, though; they're mutually exclusive).

I ran (without any connection) ```

sudo lshw -C network
```My output is like this:

```

  *-network
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:19 memory:f4000000-f4003fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:b1:62:95
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:44 ioport:5000(size=256) memory:f8610000-f8610fff memory:f8600000-f860ffff memory:f8620000-f862ffff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:22:69:3f:34:46
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-27-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

```

---

### Post by RobotGymnast on 2011-02-24
I removed my Wubi Ubuntu and installed a minimal Ubuntu version. Now I have firmware installed, and it doesn't inhibit my Windows boot from accessing any network.

However, Ubuntu still fails at connecting to encrypted networks. Unencrypted networks with or without MAC address protection are fine. However, my school network (WPA-Enterprise, AES, PEAP, MSCHAPv2, Thawte Premium CA) won't connect, and my home network (WPA2-Personal, AES) won't connect either. I feel this may be a WPA problem with my card.

Edit: Windows stopped working again. Reinstalling drivers seemed to help.

---

### Post by TBABill on 2011-02-24
Are you still using the b43 driver? I have the same wireless and b43 always causes problems like limited download speeds, hit or miss connections, flaky encrypted connections. I always use the STA (wl) driver and I have used WEP and WPA both without issue. Maybe worth a try? It's different firmware and driver, though, so the other will need to be removed/blacklisted before using the STA.

---

