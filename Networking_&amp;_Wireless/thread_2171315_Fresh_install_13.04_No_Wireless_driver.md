---
title: "Fresh install 13.04 No Wireless driver"
date: 2013-08-30
forum: Networking &amp; Wireless
---

### Post by Akshay_Vaidya on 2013-08-30
Hello,
       Installed 13.04 today. My installation lacks wifi driver. 
Specifications:

lspci

Network controller: Realtek Semiconductor Co., Ltd. Device 8179 (rev 01) **[WLAN DEVICE]**
Ethernet controller: Qualcomm Atheros QCA8171 Gigabit Ethernet (rev 10)

sudo lshw -C net

*-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:e000(size=256) memory:f7d00000-f7d03fff

Please help me install the driver

---

### Post by chili555 on 2013-08-30
Please check if this is your device: [http://askubuntu.com/questions/337785/wireless-not-working-on-toshiba-satellite-c55-a5281/337855#337855](http://askubuntu.com/questions/337785/wireless-not-working-on-toshiba-satellite-c55-a5281/337855#337855)

---

