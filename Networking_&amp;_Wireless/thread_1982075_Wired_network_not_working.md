---
title: "Wired network not working?"
date: 2012-05-17
forum: Networking &amp; Wireless
---

### Post by FrostyWolf on 2012-05-17
I am dual booting Windows 7 and XBMCbuntu on a box here. Both are brand new, fresh installs. Even in the installer for lubuntu, it was not detecting internet. Internet works 100% fine in windows.

In windows, the network adapter is listed a:
Realtek PCIe GBE Family Controller

```
lspci | grep -i realtek
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
```

```
ethtool eth0
Settings for eth0:
     Supported ports: [ TP MII ]
     Supported link modes: 10baseT/Half 10baseT/Full
                                       100baseT/Half 100baseT/Full
                                       1000baseT/Half 1000baseT/Full
     Supports auto-negotiation: Yes
     Advertised link modes: 10baseT/Half 10baseT/Full
     Advertised pause frame use: No
     Advertised auto-negotiation: Yes
     Link partner advertised link modes: 10baseT/Half 10baseT/Full
                                                         100baseT/Half 100baseT/Full
     Link partner advertised pause frame use: Symmetric Receive-only
     Link partner advertised auto-negotiation: Yes
     Speed: 10Mb/s
     Duplex: Full
     Port: MII
     PHYAD: 0
     Transceiver: internal
     Auto-negotiation: on
Cannot get wake-on-lan settings: Operation not permitted
     Current message level: 0x00000033 (51)
                                       drv probe ifdown ifup
Cannot get link status: Operation not permitted

```

---

### Post by marinara on 2012-05-18
known bug for that network chip.  I would document it, but i have no idea where to document it.
I bet you aren't using 12.04 are ya?

---

### Post by satish_j on 2012-05-18
Is the nm-applet showing network as connected?

---

### Post by psynld on 2012-09-05
I've got the same problem.

The network is connected for about 1 or 2 minutes after startup and after that it looses it's conection and can't get it back up again.
under win 7 it works without a problem.

---

### Post by marinara on 2012-09-06
known bug for that network chip.  I would document it, but i have no idea where to document it.
I bet you aren't using 12.04 are ya?

---

