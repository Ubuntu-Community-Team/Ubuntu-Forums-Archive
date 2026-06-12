---
title: "Aircrack not working"
date: 2010-06-24
forum: Networking &amp; Wireless
---

### Post by Kr8tion on 2010-06-24
When I try to run aircrack on Ubuntu 9.10, it keeps giving me a message asking if RFMON is enabled? What is RFMON and where could I look for it at? And if I don't have it, how can go about getting it?

---

### Post by msjones on 2010-06-25
try this command:

sudo airmon-ng start *interface*

Replace *interface* with your wireless device ie wlan0

This will put your wireless card into monitor mode.

---

### Post by Kr8tion on 2010-06-26
I keep getting the same thing. i use
sudo aircrack-ng eth1
turn off my network manger
sudo macchanger --xx:xx:xx:xx:xx just for a different ip address. but i don't think i'm using it right
sudo airodump-ng eth1
and this is when i get the message

---

### Post by purelinuxuser on 2010-06-26
I'd say I'm pretty familiar with the aircrack-ng suite.  But first we'll need to know your wireless card type and interface.  Post the output of the following commands:
```
lshw -c network
iwconfig
```

---

### Post by Kr8tion on 2010-06-26
Description: Wireless interface
Product:BCM4311 802.11/g WLAN
Logical name: eth1

---

### Post by realzippy on 2010-06-26
> **Kr8tion said:**
> I keep getting the same thing. i use
sudo aircrack-ng eth1
turn off my network manger
sudo macchanger --xx:xx:xx:xx:xx just for a different ip address. but i don't think i'm using it right
sudo airodump-ng eth1
and this is when i get the message

ehm,if you are not kidding,I would suggest to spend little time about some basics.E.g. setting up the driver for your broadcom wlan device
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by robbied on 2010-06-26
I had a problem using Aircrack and Macchanger together.  I didn't actually know it was Macchanger causing the problem until I read for days on the issue and found a post my someone.  I can Aircrack all day but when using Macchanger it causes some problems.

Sucks as it would be nice to hide your MAC when doing devious things. :)  Should note the victim router was my own...


EDIT: This is my setup with my hardware so this may or may not be the case with your problems.  The post that mentioned the issue didn't mention if it was specific to anything, just that Aircrack and Macchanger caused him problems.

---

### Post by purelinuxuser on 2010-06-26
> **Kr8tion said:**
> Description: Wireless interface
Product:BCM4311 802.11/g WLAN
Logical name: eth1

How did you install the driver for your device?  Did you go to System > Administration > Hardware Drivers and install the proprietary driver?

If so, then you cannot use aircrack-ng with it.  You must install the open-source driver.  To do this, deactivate the proprietary driver, get an Ethernet connection, install b43-fwcutter, and be sure the "Automatically download and install firmware?" box is **cheked**.

---

### Post by Kr8tion on 2010-06-26
Okay maybe I am skipping a step? What would be the next steps after command: sudo airmon-ng start eth1

---

### Post by purelinuxuser on 2010-06-26
> **Kr8tion said:**
> Okay maybe I am skipping a step? What would be the next steps after command: sudo airmon-ng start eth1

Usually, you would run the injection test:
```
sudo aireplay-ng -9 eth1
```
or
```
sudo aireplay-ng -9 mon0
```
The eth1 interface and the fact that you are using a Broadcom card ticks me off.  **If you installed the proprietary STA driver you CANNOT use aircrack-ng with your card.**

---

