---
title: "Can speed and duplex be manually set for eth0?"
date: 2010-05-29
forum: Networking &amp; Wireless
---

### Post by Geoff_L on 2010-05-29
Ubuntu 10.04 (Lucid Lynx)

I occasionally need to configure the speed and duplex settings for eth0 manually on my laptop. Typically this will be to troubleshoot problems on a router that I've just installed and sometimes setting both the router and my laptop to either full or half duplex and either 10 or 100 Mbps can work where auto-negotiation fails. My laptop is dual-boot Vista and Ubuntu 10.04, so I can switch to Windows where this is relatively easily done in the GUI. However, I'd rather stay in Ubuntu since everything else I need works a lot better under Ubuntu than it does under Windows.

Can anyone tell me how to change these settings?

TIA,

Geoff

---

### Post by prshah on 2010-05-29
> **Geoff_L said:**
> 
Can anyone tell me how to change these settings?


You can use mii-tool (or ethtool); quick example```
sudo mii-tool --force=100baseTx-FD eth0
```

More details available in the man pages; post back here if you need more details anyway.

---

### Post by Geoff_L on 2010-05-29
Many thanks - much appreciated. FWIW, having read the man pages, that seems to be yet another thing that Ubuntu does better than Windows!

Geoff

---

