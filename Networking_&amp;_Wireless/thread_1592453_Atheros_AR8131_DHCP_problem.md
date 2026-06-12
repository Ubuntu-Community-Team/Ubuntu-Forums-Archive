---
title: "Atheros AR8131 DHCP problem"
date: 2010-10-10
forum: Networking &amp; Wireless
---

### Post by shutyaev on 2010-10-10
I've just installed Ubuntu 10.10 Desktop (i386) on my laptop and I seem to have a network problem. My network card is correctly recognized but when it tries to get ip through DHCP from my router, it fails.

**lspci** shows:
```
03:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)
```

**ethtool -i eth0** shows:
```
driver: atl1c
version: 1.0.0.2-NAPI
firmware-version: N/A
bus-info: 000:03:00.0
```

And finally **dhclient eth0** sends half a dozen of **DHCPDISCOVER**s and ends with ```
No DHCPOFFERS received.
```

---

