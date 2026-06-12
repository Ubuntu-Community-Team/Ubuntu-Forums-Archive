---
title: "Modem not detected by wvdial.conf file on ubuntu 10.04"
date: 2011-02-05
forum: Networking &amp; Wireless
---

### Post by vijay_kansal on 2011-02-05
I want to connect my Airtel mobile broadband internet on my Ubuntu 10.04 desktop via bluetooth connection.
I am able to make a bluetooth connection between ubuntu and mobile and have created DUN using bluetooth manager.
Now, as I run the command wvdialconf /etc/wvdial.conf , output says my modem is not detected.
I ran the command lsusb
there it is indeed showing my vendor_Id etc for my modem mentioning that it is a bluetooth connection.
I tried my manually editing the file wvdial.conf using the command gedit wcdial.conf
I pasted there :

[Dialer Defaults]
Init3 = AT+CGDCONT=1,”IP”,”airtelgprs.com”,<cr>
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
ISDN = 0
New PPPD = yes
Phone = *99***1#
Modem = /dev/ttyACM0
Username = ” “
Password = ” “
Baud = 460800

and now as I ran the command wvdial
output says my modem was not detected

I am using LAVA handset with an Airtel GSM Sim to establish the connection
I am able to make internet connection on Windows7 using the same, but here on ubuntu 10.04 my Modem is not getting detected by the wvdial.conf file

Please help!!

---

### Post by vijay_kansal on 2011-02-07
any help would be highly appreciated

---

### Post by ipg on 2013-04-20
Hello Vijay,

You need to have correct Baud settings in order to make your modem to work with internet. I checked in my lappy and its 115200 for my modem.


Best Regards,
Praveen

---

### Post by wildmanne39 on 2013-04-21
Thread closed. Please do not post in old threads.

---

