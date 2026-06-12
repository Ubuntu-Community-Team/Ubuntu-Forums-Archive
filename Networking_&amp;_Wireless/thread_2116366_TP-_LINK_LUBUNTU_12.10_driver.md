---
title: "TP- LINK LUBUNTU 12.10 driver"
date: 2013-02-15
forum: Networking &amp; Wireless
---

### Post by andreas434 on 2013-02-15
Hi Im totally beginner in english and linux :)
can someone help me i need driver for tp link wn321g v4
in language for beginner :) thanks very much.

---

### Post by chili555 on 2013-02-15
I believe your device uses the driver rt2800usb that's already built in to Ubuntu 12.10. Have you inserted the device to see if it works? I suggest you do so and open a terminal and run:```
sudo modprobe rt2800usb
iwconfig
```I suspect it will just work.

---

