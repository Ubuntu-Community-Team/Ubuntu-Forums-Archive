---
title: "Do i need to install wireless firmware?"
date: 2012-04-29
forum: Networking &amp; Wireless
---

### Post by maciej234 on 2012-04-29
I installed a driver from realtek and the frimware says N/A, do I need to install anything else?  I only did a 'make install' from the downloaded firmware.  I installed non free linux firmware, and i blacklisted teh rtl8188ce, the driver is rtl8192ce.  The wireless seems to be ok now... i have the rtl8192ce setup in modules to load on startup as well.

description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 68:a3:c4:2e:b5:e1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.2.0-24-generic firmware=N/A ip=192.xxxxx  latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:2000(size=256) memory:f0500000-f0503fff

---

### Post by TBABill on 2012-04-29
If it is running adequately, no need for further action.

---

