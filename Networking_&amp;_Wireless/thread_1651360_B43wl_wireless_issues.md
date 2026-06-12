---
title: "B43/wl wireless issues"
date: 2010-12-23
forum: Networking &amp; Wireless
---

### Post by makaveli0129 on 2010-12-23
OK this is the problem that i am having: 

When using the b43-pci-bridge driver for my broadcom card i can't get the wireless to work while if i use the wl driver it does.... 

this is the only problem that i have that i can't use the wl because it doesn't allow me to change the mode of the card to monitor where as the b43 is compatible with mode change as well as with aircrack...

 This is what lspci -nnk shows:

```
06:00.0 Network controller [0280]: Broadcom Corporation BCM43XG [14e4:4329] (rev 01)
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb
```

and neither network manager or iwconfig show blank while using the b43 driver but using the wl they do work....

Any help would be appreciated!!!

---

### Post by bkratz on 2010-12-23
> **makaveli0129 said:**
> OK this is the problem that i am having: 

When using the b43-pci-bridge driver for my broadcom card i can't get the wireless to work while if i use the wl driver it does.... 

this is the only problem that i have that i can't use the wl because it doesn't allow me to change the mode of the card to monitor where as the b43 is compatible with mode change as well as with aircrack...

 This is what lspci -nnk shows:

```
06:00.0 Network controller [0280]: Broadcom Corporation BCM43XG [14e4:4329] (rev 01)
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb
```

and neither network manager or iwconfig show blank while using the b43 driver but using the wl they do work....

Any help would be appreciated!!!

Sorry, but you look to be out of luck, look at the table here.

[http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)

STA is your best way.

---

