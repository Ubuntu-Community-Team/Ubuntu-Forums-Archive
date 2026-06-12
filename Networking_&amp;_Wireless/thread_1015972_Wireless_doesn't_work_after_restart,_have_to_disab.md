---
title: "Wireless doesn't work after restart, have to disable/enable driver manually"
date: 2008-12-19
forum: Networking &amp; Wireless
---

### Post by zackdarnell on 2008-12-19
I just installed 8.10 on a Thinkpad T400 with an Atheros AR242x 802.11abg wireless PCI express adapter. Wireless was not working out of the box, so I ran:
```
sudo apt-get install linux-backports-modules-intrepid
```
This makes a new driver show up in the hardware drivers menu:
"Support for 5xxx series of Atheros 802.11 wireless LAN cards"

After disabling the default driver and enabling the new one, wireless worked. However, after a re-start, wireless does not work. The proper driver is enabled in the drivers menu, but it says "This driver is activated but is not currently in use". If I de-activate it and re-activate, it says "This driver is activated and currently in use". Any recommendations for making this work on startup, without manually having to disable and re-enable?

Or any better ways to get the wireless to work?

Thanks.

---

### Post by Shootfast on 2008-12-21
Same here. I've got an original Asus EEEPC with an Atheros wireless card and I have to disable the driver, reboot and re-enable to get wireless.
I'm also using the intrepid-backports and i've blacklisted ath_pci

---

### Post by infernowolf36 on 2008-12-21
same thing happened to me. first.. get rid of the driver. (take note that i'm not an expert in ubuntu. but this worked for me) 

connect your new ubuntu machine directly to the internet.. in other words. plug in the ethernet cord to your computer so your computer has internet access. you should have many updates for ubuntu and probably a system restart should be in order. after a bit, your ubuntu will automatically detect your wireless card. it should automatically retrieve the correct drivers AND settings. at least. that is what it did with mine. 

bottom line. just simply connect your computer to your modem and let it auto update. 

let me know your results.

---

### Post by zackdarnell on 2008-12-22
> **infernowolf36 said:**
> same thing happened to me. first.. get rid of the driver. (take note that i'm not an expert in ubuntu. but this worked for me) 

connect your new ubuntu machine directly to the internet.. in other words. plug in the ethernet cord to your computer so your computer has internet access. you should have many updates for ubuntu and probably a system restart should be in order. after a bit, your ubuntu will automatically detect your wireless card. it should automatically retrieve the correct drivers AND settings. at least. that is what it did with mine. 

bottom line. just simply connect your computer to your modem and let it auto update. 

let me know your results.Everything is updated. Still no change.

---

