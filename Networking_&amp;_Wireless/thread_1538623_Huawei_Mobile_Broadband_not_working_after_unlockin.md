---
title: "Huawei Mobile Broadband not working after unlocking."
date: 2010-07-25
forum: Networking &amp; Wireless
---

### Post by akcmails on 2010-07-25
i am using ubuntu 10.04 .
my huawei e1550 usb mobile broadband modem was detected 
out of the box and was working fine .
But after unlocking it with a software,the modem is detected and when i connect ,it immediately disconnects.
unlocking was some 'Firmware upgrade' . I tried other distros like pclinuxOs but  the same problem prevails.    
 and it is working in windows.
      please help me.

---

### Post by alexfish on 2010-07-25
hi

can you post the results of these commands from the terminal

  	 	 	 	 	 	  Code:


 [COLOR=#0000ff]lsusb[/COLOR]
 

 Code:

[COLOR=#0000ff]ls -al /dev/serial/by-id/usb*[/COLOR]

---

### Post by akcmails on 2010-07-25
[COLOR=#0000ff]results of lsusb:

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 12d1:140c Huawei Technologies Co., Ltd. 
Bus 002 Device 003: ID 04f2:b044 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

results of  ls -al /dev/serial/by-id/usb* :

lrwxrwxrwx 1 root root 13 2010-07-25 20:18 /dev/serial/by-id/usb-HUAWEI_Technology_HUAWEI_Mobile-if00-port0 -> ../../ttyUSB0
lrwxrwxrwx 1 root root 13 2010-07-25 20:18 /dev/serial/by-id/usb-HUAWEI_Technology_HUAWEI_Mobile-if01-port0 -> ../../ttyUSB1
lrwxrwxrwx 1 root root 13 2010-07-25 20:18 /dev/serial/by-id/usb-HUAWEI_Technology_HUAWEI_Mobile-if02-port0 -> ../../ttyUSB2
lrwxrwxrwx 1 root root 13 2010-07-25 20:18 /dev/serial/by-id/usb-HUAWEI_Technology_HUAWEI_Mobile-if03-port0 -> ../../ttyUSB3

thanks.
[/COLOR]

---

### Post by pdc on 2010-07-26
well .......

the ID of 

> 12d1: 140c

shows the device is switched; ie seen as a modem ..

and the ttyUSB confirms this ..........

so are you sure you have the correct apn settings in your network manager setup?

> *But after unlocking it with a software*

........ so you have gone with a new provider ???

---

### Post by akcmails on 2010-07-26
its not the problem with APN.
the modem:guitar: works now after i did some serious googling .
i found it on this site :
 [http://technolark.blogspot.com/2009/05/idea-netsetter-on-ubuntu-jaunty.html](http://technolark.blogspot.com/2009/05/idea-netsetter-on-ubuntu-jaunty.html)

it is a wvdial configuration .

thanks to all. Ubuntu rocks!!!:popcorn:

---

### Post by pdc on 2010-07-27
great!

I guess if you choose to use wvdial to connect;

and keep that card in your hand, it allows you to flourish it on the table when you choose!

enjoy ubuntu

---

