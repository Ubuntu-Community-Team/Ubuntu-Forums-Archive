---
title: "instal modem"
date: 2009-03-12
forum: Networking &amp; Wireless
---

### Post by ricardo raimundo on 2009-03-12
hello, I´m running ubuntu for the first time, and I´can´t instal the modem ZTE Modem MF620 HSDPA EDGE USB. seem that the system managed to recognize the modem, but then it did not give any more sign of life!!
What I must do?

---

### Post by miegiel on 2009-03-12
```
lsusb
``` Gives you a list of the usb hardware on your machine. If your modem is not listed the drivers might not be loaded or installed.

```
lsusb
``` Is a terminal command (see Applications > Accessories > Terminal).

Here's my list as an example:
```
:~$ lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 050d:0121 Belkin Components F5D5050 100Mbps Ethernet
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 1532:0001  
Bus 001 Device 004: ID 058f:9254 Alcor Micro Corp. Hub
Bus 001 Device 001: ID 0000:0000  
```
A usb network card and a usb hub (it's not seeing my mouse, but I'm not worried :) it's still working)

---

### Post by inobe on 2009-03-12
[https://help.ubuntu.com/8.10/internet/C/modems-adsl-usb.html](https://help.ubuntu.com/8.10/internet/C/modems-adsl-usb.html)

that's all i could find about usb modems' you should always use a modem with an ethernet connection' they are much more reliable, just my opinion of cours.

---

