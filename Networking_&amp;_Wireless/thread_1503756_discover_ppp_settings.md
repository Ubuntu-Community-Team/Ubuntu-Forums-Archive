---
title: "discover ppp settings"
date: 2010-06-07
forum: Networking &amp; Wireless
---

### Post by portia on 2010-06-07
At work I was given this Vodafone internet dongle:
```
Bus 002 Device 002: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
```

I travel a lot and don't really want to carry my windows laptop (windows xp). I much prefer to use my netbook with linux.
The dongle works out of the box on Crunchbang (based on Ubuntu). I just go to the network manager icon at the bottom of the screen and it shows: Vodafone (Contract). I click on it and that's it I'm connected.

I'm trying to set it up on slackware that is installed on the netbook using wvdial, but I don't know the number (#***), username and password. It must be some standard data, as crunchbang connects me without asking about passwords.

How can I find it out from crunchbang. I'm running it now being connected through this dongle. It uses ppp. I looked into /etc/ppp but couldn't find any data like that.

thank you in advance

---

### Post by dineshs on 2010-06-07
I guess the file will be somewhere in /etc/NetworkManager

---

### Post by iponeverything on 2010-06-07
For dial codes and provider specific information look here:

[https://wiki.ubuntu.com/NetworkManager/Hardware/3G](https://wiki.ubuntu.com/NetworkManager/Hardware/3G)

here is my /etc/wvdial.conf in case it might be of use.

root@gateway:~# cat /etc/wvdial.conf
```
[Dialer Defaults]
Init1 = ATZ
Init2 = ATZ
Init3 = AT+CPBS="SM"
Init4 = AT+CPMS="SM","SM",""
Init5 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init6 = AT+CGDCONT=1,"IP","Telstra.Internet"
Stupid Mode = yes
Modem Type = Analog Modem
Baud = 921600
New PPPD = yes
Modem = /dev/ttyUSB2
ISDN = 0
 Phone = *99#
 Password = Telstra
 Username = Telstra

```

---

