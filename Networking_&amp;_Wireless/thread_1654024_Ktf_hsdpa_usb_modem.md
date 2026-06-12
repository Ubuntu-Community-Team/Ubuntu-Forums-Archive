---
title: "Ktf hsdpa usb modem"
date: 2010-12-27
forum: Networking &amp; Wireless
---

### Post by ubunt1ous on 2010-12-27
How to connect through KTFT EV-HM100 3G HSDPA USB modem

Ubuntu 10.10

Make sure usb_storage module is not loaded

```
lsmod | grep usb
```

if it is, and you are using USB storage device, then unplug the usb storage device and unload the module.

then 

```
sudo rmmod usb_storage
```


Plug-in the 3G modem

```
lsusb
```
Bus 002 Device 002: ID 15c8:3300

```
lsusb -t
```
Port 2: Dev 2, IF 0, Class=vend., Driver=none, 12M
Port 2: Dev 2, IF 1, Class=vend., Driver=none, 12M
Port 2: Dev 2, IF 2, Class=vend., Driver=none, 12M
Port 2: Dev 2, IF 3, Class=stor., Driver=none, 12M

```
sudo modprobe option
sudo chmod a+w /sys/bus/usb-serial/drivers/option1/new_id
sudo echo "15c8 3300" >/sys/bus/usb-serial/drivers/option1/new_id

```

```
lsusb -t
```
Port 2: Dev 2, IF 0, Class=vend., Driver=option, 12M
Port 2: Dev 2, IF 1, Class=vend., Driver=option, 12M
Port 2: Dev 2, IF 2, Class=vend., Driver=option, 12M
Port 2: Dev 2, IF 3, Class=stor., Driver=option, 12M

edit the file /etc/wvdial.conf

[Dialer Defaults]
New PPPD = yes
Baud = 115200
Modem = /dev/ttyUSB0
Init1 = ATZ
Init2 = ATQ0 V1 E1 X1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","hsdpa-internet.ktfwing.com"
Init3 = AT+CFUN = 1
Stupid Mode = 1
ISDN = 0
Modem type = Analog Modem
Phone = *99#
Username = web
Password = web
Carrier Check = 0
Dial Command = ATDT
Dial Attempts = 0
Auto DNS = yes


```
sudo wvdial
```


And you should be connected.

Hope this helps, it took me nearly two months to sort it out!!!

---

