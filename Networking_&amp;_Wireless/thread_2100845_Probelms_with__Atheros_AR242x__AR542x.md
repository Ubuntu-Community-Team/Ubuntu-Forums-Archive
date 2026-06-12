---
title: "Probelms with  Atheros AR242x / AR542x"
date: 2013-01-03
forum: Networking &amp; Wireless
---

### Post by andrix10 on 2013-01-03
i have 

 Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)

and the problem is that when my phone(i use tether) is not near my laptop or the laptop is not used for like an hour, it disconnects from my phone and keeps prompting for password, even if i enter it, still prompts until i diable wireless and reanable
i dont know whats the problem, is it the drivers or something?
o and i have Ubuntu 12.04 LTS

---

### Post by vasiliscnisrok on 2013-01-03
give me
```
sudo lspci -vnnk
```

---

### Post by andrix10 on 2013-01-03
09:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Hewlett-Packard Company AR5BXB63 (Foxconn) 802.11bg Mini PCIe NIC [103c:137a]
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at d1100000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 2
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [60] Express Legacy Endpoint, MSI 00
    Capabilities: [90] MSI-X: Enable- Count=1 Masked-
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Kernel driver in use: ath5k
    Kernel modules: ath5k

---

