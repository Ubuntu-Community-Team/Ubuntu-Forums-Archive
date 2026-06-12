---
title: "Cannot connect my Huawei ER367 to Internet"
date: 2011-09-24
forum: Networking &amp; Wireless
---

### Post by suomalainen on 2011-09-24
Ubunteros,

I have a Huawei E367 broadband stick and use Ubuntu 10.04LTS. I cannot connect to the Internet.

I found this code:


1. I purchased a '3' ZTE MF112 dongle

2. I plugged it in. lsusb gives 19d2:0103

3.
* sudo aptitude install usb-modeswitch
* sudo gedit /etc/udev/rules.d/zte_eject.rules
SYSFS{idVendor}=="19d2", SYSFS{idProduct}=="0103", RUN+="/usr/bin/eject %k", OPTIONS+="last_rule"

4. reboot

5. lsusb gives 19d2:0031

6. Using NetworkManager > Edit Connections... > Mobile Broadband, I set up the dongle to access 3's network.


***************************************************************

Can the code above be manipulated so that I can use it for my E367 device?

I think it's possible and written like this??

3.
* sudo aptitude install usb-modeswitch
* sudo gedit /etc/udev/rules.d/Huawei_eject.rules
SYSFS{idVendor}=="12d1", SYSFS{idProduct}=="14ac", RUN+="/usr/bin/eject %k", OPTIONS+="last_rule"


Any suggestions to get my stick working will be appreciated. Thank you

---

### Post by suomalainen on 2011-09-24
All,

My laptop has 3 standard usb ports. I also have a PCMCIA slot. With the help of a PCMCIA card I can gain 4 additional usb ports via the card. 

When My Huawei E367 is placed into one of the slots on the card --And the laptop freshly booted-- it (E367) is detected by Network Manager and an automatic connection to the Internet is established. Yea!!!!

However, If the stick is put into one of the USB ports on the back of the laptop  -- And the Laptop freshly booted up-- Network manager does not see the device and no Internet connection can be made.

Yet, if I disconnect the Internet connection and pull the stick from the PCMCIA card and stick it into a usb port on the back of my laptop and use Network Manager to re-establish Internet connection then the Stick will work under this scenario as well. But not upon a fresh boot as noted above.

Does anyone know how I can make my stick automatically detected by Network Manager upon boot up? I'd really like to leave my stick in the back of my laptop and not have to keep pulling it out from the card each time.

Thanks everyone.

---

### Post by suomalainen on 2011-09-24
Just realised that if the stick is in one of the 3 ports upon boot up no connection to the Internet can be made. BUT upon boot up I can pull the stick out and then back in again and NOW network manager will connect to Internet... Strange isn't it? What can I do to solve this?

---

### Post by suomalainen on 2011-09-25
Good Morning everyone!

I have my Huawei E367 working but not the way it's suppose to!

When I boot up my laptop I have the stick in the usb port. Once the O/S has loaded, I must pull the stick out and then place it back in again to the usb port. Now it connects to INTERNET automatically.

What can I do so that I don't need to do this each and every time?

Thank you!

suomalainen

---

### Post by suomalainen on 2011-10-11
During the process of getting my stick to connect the O/S crashed. Re-install of 10.04 was necessary. After install stick began to work immediately.

---

