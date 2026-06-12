---
title: "Enabling Belkin USB Wireless G Adapter F5D7050A"
date: 2010-05-25
forum: Networking &amp; Wireless
---

### Post by xaxtree on 2010-05-25
So I gave up on my Belkin Wireless N Basic USB adapter because I had absolutely no luck with it, I decided to pick an adapter that had a better history...  Belkin USB Wireless G Adapter F5D7050A, But I can't seem to install it correctly, any help?  This is on a fresh install too.

---

### Post by xaxtree on 2010-05-25
Bump

---

### Post by pdc on 2010-05-26
I think this uses the RT73 driver; I suspect that is already in the kernel;

if you copy and paste 

> dmesg | grep -i RT7

can you copy and paste back what you get

---

### Post by chili555 on 2010-05-26
Please let me see:```
lsusb
```You can trim away everything that is not your Belkin, if you wish.

---

### Post by xaxtree on 2010-05-26
d3adc0d3@xyz:~$ dmesg | grep -i RT7 
[  395.810130] Registered led device: rt73usb-phy1::radio
[  395.810162] Registered led device: rt73usb-phy1::assoc
[  395.810198] Registered led device: rt73usb-phy1::quality
[  395.810759] usbcore: registered new interface driver rt73usb
[  395.906886] rt73usb 1-4:1.0: firmware: requesting rt73.bin

lsusb
Bus 001 Device 003: ID 050d:705a Belkin Components F5D7050A Wireless Adapter

---

### Post by xaxtree on 2010-05-26
ah wait nevermind! i woke up and just had a go at it on a fresh install and it worked just fine :)  sorry for the trouble :P

---

