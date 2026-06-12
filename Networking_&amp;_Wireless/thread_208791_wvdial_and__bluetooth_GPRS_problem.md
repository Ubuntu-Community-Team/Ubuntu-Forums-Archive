---
title: "wvdial and  bluetooth GPRS problem"
date: 2006-07-04
forum: Networking &amp; Wireless
---

### Post by bogoliubov on 2006-07-04
I'm trying to use my mobile phone (SonyEricsson K700i) for internet browsing via bluetooth. My laptop is an iBook G4 12" running Dapper.

To set things up I do:
hcitool scan
sdptool search DUN | grep Channel
sudo rfcomm bind 0 [MAC-adress] [Channel]

All these steps work OK (I think), but when I do
wvdial GPRS
I get:
--> WvDial: Internet dialer version 1.55
--> Cannot open /dev/rfcomm0: Connection refused
--> Cannot open /dev/rfcomm0: Connection refused
--> Cannot open /dev/rfcomm0: Connection refused

Does anyone know why I get this message and what I can do about it?

This is my wvdial.conf:
[Modem0]
Modem = /dev/rfcomm0
Baud = 57600
SetVolume = 0
Dial Command = ATDT
Init1 = ATZ
Init3 = AT+CGDCONT=1,"IP","internet.tele2.se"
FlowControl = crtscts
[Dialer GPRS]
Username =
Password =
Phone = *99***1#
Stupid Mode = 1
Inherits = Modem0

---

### Post by onizu on 2007-09-23
The problem is - your phone is not paired with your computer.

Try this:
**sudo hciconfig hci0 up**
**sudo hciconfig hci0 piscan**

This will make your computer discoverable over bluetooth. Then scan for new bluetooth devices in your phone's bluetooth pairing settings. It should detect your computer. Pair with it - enter the four digit PIN that you've set for pairing. Set it 'authorised'.

Now try your wvdial command to connect.

---

