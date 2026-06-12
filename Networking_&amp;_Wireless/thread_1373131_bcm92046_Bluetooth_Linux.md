---
title: "bcm92046 Bluetooth Linux"
date: 2010-01-05
forum: Networking &amp; Wireless
---

### Post by Keithodulaigh on 2010-01-05
Hi,
I installed Ubuntu Netbook Remix on  someone's Dell Mini 10v. I have everything working except for their bluetooth!

I poppped the service tag into Dell and it has bcm92046 as the bluetooth driver.

I've checked that bluetooth is enabled in the BIOS and the BT icon appears in the system tray but it's faded not solid. I can right click on it and go into preferences then choose enable but nothing happens!!

I searched the forum for bcm92046 but there are no results? I'm kind of surprised since I thought the mini was a popular laptop... ??

Any ideas would be appreciated.

Thanks,
Keith

---

### Post by KukMan on 2010-11-27
I have Acer Aspire 1551 netbook. It has bluetooth adapter, which not recognized. On the label at the bottom of netbook writes, that it use Foxconn BCM92046 Bluetooth adapter. I can't see it in lspci or lsusb outputs. Does linux supports this adapter?

---

### Post by Hippytaff on 2010-11-27
Broadcom can be a pain, it might involve using Ndiswrapper to install the windows xp driver, blacklisting and with usb wireless devices modeswitching...I'm searching the forums now, but there is loads of info here if you search :-) common issue :-)

---

