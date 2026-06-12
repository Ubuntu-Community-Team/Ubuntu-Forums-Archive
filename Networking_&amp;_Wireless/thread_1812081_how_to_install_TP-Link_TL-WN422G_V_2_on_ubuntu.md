---
title: "how to install TP-Link TL-WN422G V 2 on ubuntu ??"
date: 2011-07-25
forum: Networking &amp; Wireless
---

### Post by vii_vach on 2011-07-25
Hey guys I need to know that how should I install my usb Wireless adaptor , it's a tplink tl-wn422g v 2 , is there any way to install it ? :confused::confused:

---

### Post by wildmanne39 on 2011-07-25
Hi, please run these commands in a terminal.
```
lsusb
```
```
lsmod
```
```
sudo lshw -C network
```
```
iwconfig
```
```
rfkill list all
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by vii_vach on 2011-07-26
Hi mate thanks for your Attention about my question , but i found the solution to how to install my wireless adaptor . It's so easy and simple ! I just upgrade from Ubuntu v 10.10 to latest version 11.04 (Plug and Play) . My wireless is now working perfect as on win !
I think this problem had been solved on ubuntu v 11.04 .

any way thanks again 
CHEERS ! :D:lolflag:

---

### Post by wildmanne39 on 2011-07-26
Hi, your welcome! would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

