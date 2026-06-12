---
title: "Mobile broadband, Kubuntu 10.10."
date: 2010-10-16
forum: Networking &amp; Wireless
---

### Post by gnush on 2010-10-16
Hey there.
I felt like installing Kubuntu 10.10, but I can't get my mobile broadband to work. It's recognized, but it won't connect.
It doesn't ask for PIN either, which it does on Ubuntu 10.04.

What could be the problem?

---

### Post by alexfish on 2010-10-16
hi

can you post results of this command from the terminal

Code:

[COLOR=Blue]usb-devices[/COLOR]

find the parts of the device and post only those parts

alexfish

---

### Post by gnush on 2010-10-16
```
T:  Bus=01 Lev=01 Prnt=01 Port=05 Cnt=01 Dev#= 12 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1001 Rev=00.00
S:  Manufacturer=HUAWEI Technology
S:  Product=HUAWEI Mobile
C:  #Ifs= 5 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

```


This is done in Ubuntu 10.04, do you want me to boot up Kubuntu and run the command there?

---

### Post by alexfish on 2010-10-16
[COLOR=Blue][COLOR=Black]seems OK

now need to see if ttyports are configured

Code:[/COLOR]

ls -al /dev/serial/by-id/usb*

[COLOR=Black]find if modem manager on system


Code:

[COLOR=Blue]which modem-manager


[/COLOR][/COLOR]



[/COLOR]

---

### Post by arunce on 2010-12-11
usb-devices

```

T:  Bus=05 Lev=01 Prnt=01 Port=01 Cnt=02 Dev#=  9 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=0001 Rev=00.00
S:  Manufacturer=Qualcomm, Incorporated
S:  Product=ZTE CDMA Technologies MSM
C:  #Ifs= 3 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option

```which modem-manager
```

/usr/sbin/modem-manager

```ls -al /dev/serial/by-id/usb*
```

lrwxrwxrwx 1 root root 13 2010-12-11 21:46 /dev/serial/by-id/usb-Qualcomm__Incorporated_ZTE_CDMA_Technologies_MSM-if00-port0 -> ../../ttyUSB0
lrwxrwxrwx 1 root root 13 2010-12-11 21:46 /dev/serial/by-id/usb-Qualcomm__Incorporated_ZTE_CDMA_Technologies_MSM-if01-port0 -> ../../ttyUSB1
lrwxrwxrwx 1 root root 13 2010-12-11 21:46 /dev/serial/by-id/usb-Qualcomm__Incorporated_ZTE_CDMA_Technologies_MSM-if02-port0 -> ../../ttyUSB2

```

I've all setup in Network Manager but can't connect. :confused:

---

### Post by alexfish on 2010-12-11
Hi
all the output seem ok

normaly this ZTE device connects on Base 00 : IE dev/ttyUSB0

it is possible for any connection manager relying on rules to connect to this port

zte port rules
ATTRS{idProduct}=="0001", ENV{.MM_USBIFNUM}=="00", ENV{ID_MM_ZTE_PORT_TYPE_MODEM}="1"
ATTRS{idProduct}=="0001", ENV{.MM_USBIFNUM}=="02", ENV{ID_MM_ZTE_PORT_TYPE_AUX}="1"

can you check the port rules on your system

grep "0001" /lib/udev/rules.d/77-mm-zte-port-types.rules

if the rules are OK

double check the info for the connection is correct

have you also tried kppp

Can also post full details of the Computer / laptop or pc/ do you know if your system has a Gobi/qualcomm

chipset

---

### Post by arunce on 2010-12-12
It's working. 

I didn't change anything else, just a reboot, and when I plugged the usb modem it started working after a few seconds.

**Maybe some Network Management configuration file needed a reload, not sure.**

Btw, my rules are equal to your example.


Now I need to setup tethering (bluetooth via win 6.1 phone), but I'm not sure about Network Management support, any recommendations?  (links, docs)
 
I'm using Kubuntu 10.10 with KDE 4.5.4 from PPA Rep.

Thank you.

---

### Post by alexfish on 2010-12-12
hi

have you looked under System / Preferences/Bluetooth

can also have a look here

[http://www.pcurtis.com/ubuntu-mobile.htm](http://www.pcurtis.com/ubuntu-mobile.htm)

there is also a prog called blueman in the repos


alexfish

---

