---
title: "ubuntu 9.10 disable network interface from command line"
date: 2010-03-17
forum: Networking &amp; Wireless
---

### Post by marwan.alsabbagh on 2010-03-17
Hi, I'm trying to disable/enable my network interface through the command line. I would like to do it through the command line so that I can automate it. looking at some [older Ubuntu docs]("https://help.ubuntu.com/8.10/internet/C/networking-disable.html") the command is meant to be as follows:
```
sudo ifdown eth2
```
but when I run it I get the error **Ignoring unknown interface eth2=eth2**. running ifconfig shows me the network interface is called eth2. I can of course disable and enable the interface through the GUI using network manager. thanks for the help guys.

---

### Post by mikewhatever on 2010-03-17
Try the following:

sudo ifconfig eth2 down

..and to re-enable

sudo ifconfig eth2 up

---

### Post by marwan.alsabbagh on 2010-03-17
fantastic! works perfectly. I love Ubuntu. thanks for the quick reply!

---

### Post by Cupster on 2011-05-14
thanks for this info!
just what I needed :)

---

