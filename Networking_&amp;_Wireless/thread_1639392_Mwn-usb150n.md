---
title: "Mwn-usb150n"
date: 2010-12-06
forum: Networking &amp; Wireless
---

### Post by Inquirer002 on 2010-12-06
Hi. I am new to Ubuntu, just downloaded it, and booting it from a USB drive. 
The wireless adapter that comes with my computer as some issues, so I bought the Medialink MWN-USB150N usb wireless adapter. The problem is that I have no idea how to install the driver. Ubuntu detected my in-build wireless card and downloaded the driver for that, but it doesn't seem to detect my usb wireless adapter. 

Any help on how to find the driver, and how to install them, would help. Thanks :)

---

### Post by deltacomp on 2011-11-07
Hello. Hopefully you have already resolved this issue seeing it has been over a year. If you have not, please follow below. 

Download the drivers from this [link]("http://www.medialinkproducts.com/support.php").

Go to the file where the you downloaded the driver (likely downloads). Right click on it and use archive manager to extract the file. 
Extract the file to your home folder. 
Open a terminal and copy and paste the following into the terminal;

cd  ~/2009_0525_RT3070_Linux_STA_v2.1.1.0 (hit enter)

make (hit enter)

Then you are done. This should install the necessary drivers for your USB adapter. 

Good Luck

---

### Post by StrobeWylan on 2012-08-04
> **deltacomp said:**
> 
Open a terminal and copy and paste the following into the terminal;

cd  ~/2009_0525_RT3070_Linux_STA_v2.1.1.0 (hit enter)

make (hit enter)

Then you are done. This should install the necessary drivers for your USB adapter. 

Good Luck

Hello. I know this is an older post, but I'm old and therefore a bit slow.
I just put Ubuntu 10.04 on a friends HP pavilion "Entertainment" laptop. everything works fine, hooked up to my Ethernet (did I mention that I am old?).
He has a wireless hookup in his place. I'm trying to get his Mwn-usb150n to work. After running your steps in terminal I got the message "[Linux] error 2"

Thanx to anyone who can help. (Please keep it simple)

---

### Post by chili555 on 2012-08-04
> **StrobeWylan said:**
> Hello. I know this is an older post, but I'm old and therefore a bit slow.
I just put Ubuntu 10.04 on a friends HP pavilion "Entertainment" laptop. everything works fine, hooked up to my Ethernet (did I mention that I am old?).
He has a wireless hookup in his place. I'm trying to get his Mwn-usb150n to work. After running your steps in terminal I got the message "[Linux] error 2"

Thanx to anyone who can help. (Please keep it simple)Speaking of old...this is a pretty old thread and you are probably not older than old Dr. Chili. Please start your own new thread and post:```
lsusb
```There may be an easier way.

---

