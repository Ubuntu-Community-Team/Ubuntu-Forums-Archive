---
title: "Which USB Wifi 802.11g adapter to buy?"
date: 2006-04-14
forum: Networking &amp; Wireless
---

### Post by guzzi333 on 2006-04-14
Hi,

I want to buy a USB wifi 802.11g network adapter which works out of the box with ubuntu. I don't want to buy a a network adapter for which I need to install the windows driver, because
1. I don't want to mess around with Windows drivers and ndiswrapper etc. It should work out of the box
2. I want to support hardware manufacturers that make linux compatible hardware.

Any recommendations?

Thanks

---

### Post by SickTwist on 2006-04-14
Something with the Atheros chipset should work well with Ubuntu. The Linux driver for this chipset is called "madwifi" and is included with Ubuntu. You may wish to check out the [MadWiFi project website]("http://madwifi.org/") to see if there is an updated list of devices currently shipping with that chipset.

Also, be sure to look not only at the model number, but at the hardware revision number (often printed on the box) as well when purchasing your wireless adapter. Sometimes manufacturers will change chipsets without changing a product's model number. Best of luck!

---

### Post by guzzi333 on 2006-04-15
Just found this 
[http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

I guess I'm going for the belkin

---

### Post by guzzi333 on 2006-06-03
OK the Belkin did not work. They changed the chipset. ](*,) 

Now I bought an ASUS WL-167G and that one works out of the box with Dapper :D 

Only needed to add

alias rausb0 rt2570 

to /etc/modprobe.d/aliases

---

