---
title: "Wireless not working in 10.04"
date: 2010-06-01
forum: Networking &amp; Wireless
---

### Post by Zwendel on 2010-06-01
About 9 hours ago I installed Ubuntu 10.04 on a MSI laptop and since then I tried numerous things to get my wireless up and running, but no luck what so ever.

- the ath5k driver seemed to be working, but could not find any wireless networks
- the madwifi driver, I got up and running perfectly, according to system->administration->Hardware Drivers that is, but also, no luck finding any wireless networks (yet, I have several networks up that I should be able to find, checked them via Windows)
- I reinstalled Ubuntu and then tried the ndiswrapper but the wlan0 doesn't show up via iwconfig, yet according to ndiswrapper:
```
net5211 : driver installed
	device (168C:001C) present (alternate driver: ath5k)
```
When I look at the log I see a -22 error which I googled and it appears to be an IRQ error. The IRQ is already in use by a USB port

lshw -C network shows:
  ```
*-network UNCLAIMED     
       description: Ethernet controller
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:fd7f0000-fd7fffff
```

How on earth do I get this wireless Atheros card to work with 10.04?

---

