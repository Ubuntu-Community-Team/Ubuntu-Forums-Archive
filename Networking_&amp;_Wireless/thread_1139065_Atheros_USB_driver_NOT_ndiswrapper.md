---
title: "Atheros USB driver *NOT* ndiswrapper"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by rob356 on 2009-04-26
I have gotten my wireless adapter (Netgear WG111t, atheros chipset) working in ubuntu using Ndiswrapper. BUT, I would like to use monitor mode, and as I have read Ndiswrapper will never support this because NDIS drivers will never. 

What I would like to know is if anyone has found a driver for usb atheros devices, that is not ndiswrapper. Madwifi will not work because they say they don't support usb devices.

Thanks

---

### Post by SuperSonic4 on 2009-04-26
Does ath5k not work?

---

### Post by rob356 on 2009-04-26
does ath5k support USB devices? 
I removed the ndiswrapper module and loaded the ath5k module and nothing happened. But then again when I do lsusb it shows nothing about atheros, just netgear. 
Has anyone gotten ath5k to work on USB devices?

---

### Post by PatTang on 2009-04-27
What windows driver did you use to under ndiswrapper to get this working?
Im trying to get a wn821n running but the windows drivers dont work for this.

---

### Post by kevdog on 2009-04-27
Unless Im way out in left field I thought ath5k was only for pci devices!

---

### Post by marubotti on 2009-04-28
Hello, im new in ubuntu and i want to buy a wireles card pci, but that car may support monitor mode, and i don´t know wich ist the correct for that.

thanks a lot! im from Argenitna, Cordoba.

---

### Post by rob356 on 2009-04-28
> **PatTang said:**
> What windows driver did you use to under ndiswrapper to get this working?
Im trying to get a wn821n running but the windows drivers dont work for this.
I Used the driver from Netgear, I installed it in windows, and went and collected the files it installed. You should have at least an .INF file and .SYS file.

> Hello, im new in ubuntu and i want to buy a wireles card pci, but that car may support monitor mode, and i don´t know wich ist the correct for that.

thanks a lot! im from Argenitna, Cordoba.

If you are using CardBus on a laptop, the [D-Link WNA-1330](http://www.amazon.com/D-Link-WNA-1330-802-11g-Wireless-Cardbus/dp/B000NW5VJU/ref=sr_1_1?ie=UTF8&s=electronics&qid=1240932660&sr=8-1) works great with ath5k, and monitor mode, I use it in my laptop.

---

### Post by n_s_simpson on 2009-10-24
Did anyone manage to get the WG111T into monitor mode?

---

