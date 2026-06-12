---
title: "Trying to get Belkin FD6020 wireless to work on latest kernel"
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by piazz on 2008-12-30
Hello,

noob here, trying to get a Belkin wireless card FD6020ver2 to work on a new minimal install using Xfce. This card has worked automatically on a previous version of Ubuntu so I've not installed it before manually. I've downloaded what I think is the correct driver/package - atmelwlandriver - but not sure where to go from here.

The first question should be - will it work? According to [this]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin#PCMCIA") it does not work on any kernel later than 2.6.12 (I have 2.6.27). If not then I need to get a new card or try a different distro (I need to have a 'fast' system on this old Dell Latitude as it's at a max of 256MB RAM).

iwconfig - gives 'no wireless extensions' for lo and eth0.

lspci - not sure what info is required from this but it shows Ethernet controller: 3Com 3c556 Hurricane CardBus.

lsmod - shows modules used by atmel_cs.

dmesg - what should I look for here?

---

