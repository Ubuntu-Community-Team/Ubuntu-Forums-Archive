---
title: "Wireless without ndiswrapper???"
date: 2010-09-23
forum: Networking &amp; Wireless
---

### Post by jtricer1973 on 2010-09-23
Hey guys, I have an gateway laptop with Ubuntu Lucid on it. Everything works but the webcam screws up ndiswrapper when I install cheese so I can't use my webcam and have wireless access. Can I get my wireless to work without ndiswrapper. I have a realtek 8101e/8012e wireless. Is there maybe a driver I could download and install without using ndiswrapper?

Thanks in advance.

---

### Post by jtricer1973 on 2010-09-23
Sorry guys, the realtek thing I listed above is the ethernet. Here is my lsusb


Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 04f2:b027 Chicony Electronics Co., Ltd Gateway USB 2.0 Webcam
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by BkkBonanza on 2010-09-24
I have a Realtek 8187B wifi dongle and never used Ndiswrapper with it. You should be able to use rtl8187 drivers. At least I am and it works fine with my webcam (on Acer laptop). I just fired up Cheese to test with the dongle plugged in.

Edit - just checked again, mine isn't a B model. If you really need ndis for the B model then I'd say it isn't worth the hassle. Just swap in a better adapter. They are so cheap nowadays on ebay. I've bought several there. This RT8187 cost < $10, and an [Intel 4965]("http://shop.ebay.com/i.html?_nkw=intel+4965+pci+&_cqr=true&_nkwusc=intel+4965+miniPCIe&_rdc=1") (miniPCIe) can be had for $12.99 inc shpg. and works great.

---

