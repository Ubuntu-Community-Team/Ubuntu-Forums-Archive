---
title: "Connecting Qualcomm modem to ubuntu"
date: 2012-01-13
forum: Networking &amp; Wireless
---

### Post by niladrithedon on 2012-01-13
Hello friends I am running ubuntu 10.10 on wubi and I am a new to linux. I am trying to connect my Qualcomm 2000 (linktop 3197) cdma 1x usb modem. I have tried ndiswrapper, edited the wvdial.conf file by the manufacturer specifications even tried instaling drivers from them. But so far no help. sakis3g wont work as its cdma. 
Heres the output coming from lsusb-
Bus 004 Device 002: ID 05c6:3197 Qualcomm, Inc CDMA Wireless Modem/Phone
Thanx in advance.

---

### Post by niladrithedon on 2012-01-13
by the way its not qualcomm gobi 2000. mine is a external usb cdma modem. any help is mostly appreciated.

---

### Post by alexfish on 2012-01-13
can post the results of this command from the terminal

```
usb-devices
```

alexfish

---

### Post by niladrithedon on 2012-01-14
Its like this. I am giving only the relevant section-
T:  Bus=04 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=16 #Cfgs=  1
P:  Vendor=05c6 ProdID=3197 Rev=00.00
S:  Manufacturer=Qualcomm, Incorporated
S:  Product=Qualcomm CDMA Technologies MSM
C:  #Ifs= 2 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=moto-modem
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=moto-modem

Thanx anyway

---

### Post by alexfish on 2012-01-14
hi

The drivers have loaded for the device,
need to see if device will list by-id

from the teminal
```
ls -al /dev/serial/by-id
```post the results

have you tried to use Network Manager for the connection , modem-manager should have the plug-in for this device

---

### Post by niladrithedon on 2012-01-14
I have tried the Network Manager. It detects my device. Even after entering my phone number, username and password it tries to connect for some time But it doesnt get connected. 
Here's the output you asked for
total 0
drwxr-xr-x 2 root root 80 2012-01-15 08:08 .
drwxr-xr-x 4 root root 80 2012-01-15 08:08 ..
lrwxrwxrwx 1 root root 13 2012-01-15 08:08 usb-Qualcomm__Incorporated_Qualcomm_CDMA_Technologies_MSM-if00-port0 -> ../../ttyUSB0
lrwxrwxrwx 1 root root 13 2012-01-15 08:08 usb-Qualcomm__Incorporated_Qualcomm_CDMA_Technologies_MSM-if01-port0 -> ../../ttyUSB1

Thanx friend:o:o:o:o:o

---

### Post by alexfish on 2012-01-15
hi 
indications are this driver is for "(0x05c6, 0x3197) }, ***/* unknown Motorola phone */" . extract form moto-modem.c***
**** 
*so not sure if the correct driver but will look at this later*
 
can go to
[[IMG]http://ubuntuforums.org/images/misc/paperclip.gif[/IMG]]("http://ubuntuforums.org/search.php?searchid=85034637#") [How To : Mobile Broadband Connections [ Ubuntu 11.04 : 10.10 : 10.04 : 9.10]]("http://ubuntuforums.org/showthread.php?t=1466490")
 
find the lines **TESTING MODEM-MANAGER.**
 
post the resuts of the test . 
 
alexfish

---

