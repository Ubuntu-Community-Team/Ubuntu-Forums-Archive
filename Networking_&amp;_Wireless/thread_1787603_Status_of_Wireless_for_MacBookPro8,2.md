---
title: "Status of Wireless for MacBookPro8,2"
date: 2011-06-21
forum: Networking &amp; Wireless
---

### Post by Lars Noodén on 2011-06-21
I have a MacBookPro8,2 with Natty and I would like to get the wireless networking running.  Where should I look for materials on how to do that?

---

### Post by chili555 on 2011-06-21
You can start by googling the identity of your wireless card:```
lspci -nn
```We can help you through the process if that's more convenient.

---

### Post by Lars Noodén on 2011-06-21
Thanks.

```

00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)
00:01.0 PCI bridge [0604]: Intel Corporation 2nd Generation Core Processor Family PCI Express Root Port [8086:0101] (rev 09)
00:01.1 PCI bridge [0604]: Intel Corporation 2nd Generation Core Processor Family PCI Express Root Port [8086:0105] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation 6 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
00:1a.0 USB Controller [0c03]: Intel Corporation Device [8086:1c2c] (rev 05)
00:1a.7 USB Controller [0c03]: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 6 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b5)
00:1c.1 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 2 [8086:1c12] (rev b5)
00:1c.2 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 3 [8086:1c14] (rev b5)
00:1d.0 USB Controller [0c03]: Intel Corporation Device [8086:1c27] (rev 05)
00:1d.7 USB Controller [0c03]: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 05)
00:1f.0 ISA bridge [0601]: Intel Corporation HM65 Express Chipset Family LPC Controller [8086:1c49] (rev 05)
00:1f.2 IDE interface [0101]: Intel Corporation 6 Series Chipset Family 4 port SATA IDE Controller [8086:1c01] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series Chipset Family SMBus Controller [8086:1c22] (rev 05)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc NI Seymour [AMD Radeon HD 6470M] [1002:6760]
01:00.1 Audio device [0403]: ATI Technologies Inc Device [1002:aa98]
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe [14e4:16b4] (rev 10)
02:00.1 SD Host controller [0805]: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader [14e4:16bc] (rev 10)
**03:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4331] (rev 02)**
04:00.0 FireWire (IEEE 1394) [0c00]: Agere Systems FW643 PCI Express1394b Controller (PHY/Link) [11c1:5901] (rev 08)

```

---

### Post by chili555 on 2011-06-21
Please see: [http://ubuntuforums.org/showthread.php?p=10964806#post10964806](http://ubuntuforums.org/showthread.php?p=10964806#post10964806)

Also see: [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

[http://www.spinics.net/lists/linux-wireless/msg66140.html](http://www.spinics.net/lists/linux-wireless/msg66140.html)> So yes, it looks like new BCM4331 chipset. AFAIK there is no support
for it in wl. Plus no support in b43 or brcm80211.


I'm still looking...

---

### Post by Lars Noodén on 2011-06-21
So the relevant section of lspci was this, right?

03:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4331] (rev 02)

---

### Post by chili555 on 2011-06-21
> **Lars Noodén said:**
> So the relevant section of lspci was this, right?

03:00.0 Network controller [0280]: Broadcom Corporation Device [[COLOR="Red"]14e4:4331[/COLOR]] (rev 02)That's correct. It is not claimed by any known Broadcom driver. You could try ndiswrapper however, the reports are not encouraging:  [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

[http://webcache.googleusercontent.com/search?q=cache:b4f-YC1WFigJ:ubuntuforums.org/showthread.php%3Ft%3D1695746%26page%3D2+ndiswrapper+broadcom+4331&cd=1&hl=en&ct=clnk&gl=us&source=www.google.com](http://webcache.googleusercontent.com/search?q=cache:b4f-YC1WFigJ:ubuntuforums.org/showthread.php%3Ft%3D1695746%26page%3D2+ndiswrapper+broadcom+4331&cd=1&hl=en&ct=clnk&gl=us&source=www.google.com)

---

