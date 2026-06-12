---
title: "wireless modem"
date: 2010-01-15
forum: Networking &amp; Wireless
---

### Post by adiepati on 2010-01-15
ubuntu I can not use a wireless modem huawei 160.type can only be used in windows.well to be used in my ubuntu linux? whether there is a script that used .please help me ...
:(

---

### Post by superprash2003 on 2010-01-15
you connect to this wifi modem wirelessly right? if so post output of the following from the terminal
1)ifconfig
2)iwconfig
3)sudo iwlist scanning

---

### Post by pdc on 2010-01-16
I think this is likely to be this device

[http://www.huawei.com/mobileweb/en/products/view.do?id=1960](http://www.huawei.com/mobileweb/en/products/view.do?id=1960)

if so, it is a 3G modem

if you copy and paste these commands into a terminal;

you should find the terminal in the Accessories menu

> lsusb

and 

> uname -r

and copy and paste the results back to us

you are using Ubuntu 9.10 ?

**_have a read at this post from about half-way down the page_** where it says

"**_Create a mobile broadband connection_**":

Try it out;

does any of this work for you?

[http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html](http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html)

---

