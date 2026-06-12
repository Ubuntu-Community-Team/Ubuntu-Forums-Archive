---
title: "Wireless Problem"
date: 2010-03-19
forum: Networking &amp; Wireless
---

### Post by VampiricPadraig on 2010-03-19
Hello, I have a RT2500 Wireless card and everytime I start Ubuntu, I have to remove the USB Dongle and when I log in, I plug it in and it works.
 
Is there a way around this. It's driving me bananas.
 
Thanks in advance

---

### Post by chili555 on 2010-03-19
Please let us see, in a terminal, with the device inserted:```
lsusb
lsmod | grep -e rt2 -e rt3
```Thanks.

---

