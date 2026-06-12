---
title: "Connection with Huawei E1550"
date: 2010-12-24
forum: Networking &amp; Wireless
---

### Post by techkom on 2010-12-24
Help me!!!!!
i can't connect to internet using modem Huawei E1550 (Ubuntu 8.04 Hardy Heron)

i have test usb_modeswitch
it did'nt work

vendor and product number bla bla bla (i don't remember)
and if i use wvdial
no modem detect!

lsusb


Bus 003 Device 012: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
Bus 003 Device 011: ID 0a5c:2100 Broadcom Corp. Bluetooth 2.0+eDR dongle
Bus 003 Device 010: ID 0951:1653 Kingston Technology 
Bus 003 Device 009: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 003 Device 008: ID 0457:0151 Silicon Integrated Systems Corp. Super Flash 1GB / GXT  64MB Flash Drive
Bus 003 Device 002: ID 0e8f:0016 GreenAsia Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1267:0210 Logic3 / SpectraVideo plc 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

and what i do

:(

gnome ppp did'nt help
it same 
did'nt have modem driver

scanModem it did'nt works anymore

HOW CAN I DETECT MODEM DRIVER?
and
HOW CAN I CONNECT TO THE INTERNET??

(sorry my english is bad)

o yea
i have used BlankOn 3.0 lontara
it based on Ubuntu 8.04 Hardy Heron

---

### Post by annu2127 on 2011-03-09
Hello,
         I have done this, but with Ubuntu Lucid 10.04....hope things will work for u too...just follow the steps below...
install the package usb_modeswitch 

$ sudo apt-get install usb_modeswitch

& then create a new rule for udev:

$ sudo gedit /etc/udev/rules.d/15-huawei-155x.rules
 

copy & paste the following in the file opened:
 

SUBSYSTEM=="usb",
ATTRS{idProduct}=="1446",
ATTRS{idVendor}=="12d1",
RUN+="/lib/udev/modem-modeswitch --vendor 0x$attr{idVendor} --product 0x$attr{idProduct} --type option-zerocd"


save the file & close, after this, u just need to plug ur modem....it will be detected automatically.


Next step is to create a mobile broadband connection. Go to system > Preferences > Network Connections. In the Mobile Broadband tab add a New Connection (Specific to your Service Provider..i am using Airtel)....&  then from the notification area, make the connection. :popcorn:

---

