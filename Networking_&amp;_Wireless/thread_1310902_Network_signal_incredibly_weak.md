---
title: "Network signal incredibly weak"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by J V on 2009-11-02
The network signal here is incredibly weak, I would give a screenshot but the window steals focus and the screenshot is never made...

Basicly I'm broadcasting a network to NAT my PS3, unfortunately, the signal is extremely low (like sub-10% low) and that's from the PC that's *emiting* it...

My only guess is that something is wrong with the card or driver and its just a lemon... But I can't take it back and don't want to so does anyone have an idea?

```
# lshw:
  *-network
       description: Wireless interface
       product: RT2800 802.11n PCI
       vendor: RaLink
       physical id: 9
       bus info: pci@0000:07:09.0
       logical name: ra0
       version: 00
       serial: 00:0c:f6:43:b0:de
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 ip=10.42.43.1 latency=32 maxlatency=4 mingnt=2 module=rt2860sta multicast=yes wireless=RT2860 Wireless
```

---

