---
title: "PCI Card"
date: 2006-03-12
forum: Networking &amp; Wireless
---

### Post by swooshvapors13 on 2006-03-12
Does anyone know if the Linksys Wireless g Desktop card (WMP54G) is compatable with Ubuntu? If it is, could someone please give me directions on how to install it? Thanks so much!

---

### Post by Lambert on 2006-03-12
this card looks to use a broadcom chipset. If that's so then there is no stable driver that can be used in Breezy that's native.

You can use an app called ndiswrapper to get the windows drivers to work in linux.

Here is a starting link. 
[http://doc.gwos.org/index.php/LinuxWirelessDrivers]("http://doc.gwos.org/index.php/LinuxWirelessDrivers")

If it's broadcom you will want to follow these instructions.

[https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper)

---

