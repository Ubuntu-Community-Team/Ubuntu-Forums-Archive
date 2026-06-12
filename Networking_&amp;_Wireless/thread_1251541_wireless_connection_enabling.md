---
title: "wireless connection enabling"
date: 2009-08-27
forum: Networking &amp; Wireless
---

### Post by Helend on 2009-08-27
I am still able to connect to wireless when I restart with windows, but in Ubuntu I can't select "wireless" connections in the drop-down menu when I click on the network icon at the top right corner.  The Wireless, wired, and disconnect options are all greyed out.  HELP!

---

### Post by SoftwareExplorer on 2009-08-27
It could be a couple of things:

1. There is not a native Linux driver for your wireless card. If this is the case, you could use ndiswrapper. It will use a windows driver and 'translate' from windows to linux.

2. There is a linux driver, but it isn't installed by default.

3. The driver is installed by default, but it isn't working properly. 

I've listed them in order from most likely to least. 

Also, could you go to Applications->Accessories->Terminal and run ```
lspci
```and ```
lsusb
``` and post the output here? That will tell people what kind of hardware you have and help them give you advice accordingly.

---

### Post by wareagle on 2009-08-27
Go to system, administration, hardware drivers.

It will tell you if you need to install restricted drivers for your card.

---

